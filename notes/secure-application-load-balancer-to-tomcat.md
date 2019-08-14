![secure](https://silvrback.s3.amazonaws.com/uploads/3e1daec1-97c7-4abb-81a1-42da1b206df7/secure.jpg)

The engineering team at my company recently realized that we can greatly benefit from an active-active architecture. The solution we settled on was launching multiple instances (two to start) behind a load balancer. We're on AWS, so we're using an ALB (application load balancer) and EC2. We also need encrypted communication all the way down, so we need TLS encryption at the load balancer as well as between the load balancer and the instances. Yes, AWS is built on security, but due to requirements by customers we need to encrypt all the traffic ourselves.

On the surface the requirements are:

(For each environment)
- Launch a second instance that matches the current one
	-- Remove apache
- Add certificate to instance(s)
- Create a target group (with adequate health check)
- Create an ALB
	-- Add certificate to ALB
	-- Configure networking to use secure ports

Let's get started!

---
## Remove Apache
Our application runs in Tomcat, behind Apache HTTP server. But, because the Apache server is doing the same work the ALB will do for us, we can bypass that and send traffic straight from the ALB to Tomcat.

Now that we have our new instance (from a previously generated AMI), we need to remove Apache. 
Taking a look at all running services
```service --status-all``` 
There it is
```[ + ]  apache2```
We'll stop it
```sudo service apache2 stop```
Ok, it is stopped
```[ - ]  apache2```
Because we installed it manually, let's find where it lives
```whereis apache2```
```apache2: /usr/sbin/apache2 /usr/lib/apache2 /etc/apache2 /usr/share/apache2 /usr/share/man/man8/apache2.8.gz```
Let's delete those directories and files
```sudo rm -rf /usr/sbin/apache2 /usr/lib/apache2 /etc/apache2 /usr/share/apache2 /usr/share/man/man8/apache2.8.gz```
Trust but verify
```whereis apache2```
Yep, gone
```apache2:```

---
## Add Let's Encrypt Certificate
Our instances previously had certbot installed and LE certificates installed in Apache. Now, we need different certificates because we have two instances (with different IPs) and to use them in Tomcat.
#### Generate a Certificate
Certbot makes this really simple
```sudo certbot certonly --standalone -d DOMAIN```
#### Add Certificate to Tomcat Config
Copy the ```cert.pem```, ```chain.pem```, ```privkey.pem``` files to ```/opt/tomcat/conf``` and give Tomcat ownership: ```chown tomcat:tomcat /opt/tomcat/conf/*.pem```. This step is annoying when it comes to renewing the certificate, but as far as I've found Tomcat will not allow you to use symlinks in the config for a Connector. A workaround is to run a script to copy (and restart if you're ok with that) as a renew post hook.
Uncomment (or delete) the 8443 Connector block in the /opt/tomcat/conf/server.xml and change it to
```<Connector port="8443"
	       protocol="org.apache.coyote.http11.Http11NioProtocol"
	       maxThreads="200"
	       scheme="https"
	       secure="true"
	       SSLEnabled="true"
	       SSLCertificateFile="conf/cert.pem"
	       SSLCertificateKeyFile="conf/privkey.pem"
	       SSLCertificateChainFile="conf/chain.pem"
	       SSLVerifyClient="optional"
	       SSLProtocol="TLSv1+TLSv1.1+TLSv1.2" />
```
and restart Tomcat: ```systemctl restart tomcat```
Now Tomcat has a connector setup for port 8443 that will use the certificate.
**Remember**
LE certificates expire after 90 days and will need to be renewed. This can be done automatically using certbot, but you'll also have to copy the certificates over and restart Tomcat.

---
## Create Target Group
We need a way to tell the ALB where our instances are and which ones to use. This is a target group. Doing so in the AWS console requires only a couple of steps. For our purposes, we need the traffic to use port 8443 where we're encrypting it using TLS.
![Silvrback blog image ](https://silvrback.s3.amazonaws.com/uploads/95098134-44bf-4f9d-abc7-f82b9de1948c/target-group.png)

---
## Create ALB
Creating and configuring an ALB is pretty minimal, so we'll focus on where the guts of the load balancer lie: the listeners.
#### Listeners
The default is HTTP on port 80, but we don't want to allow insecure access. We can change the default action to redirect to port 443.
![default ALB action](https://silvrback.s3.amazonaws.com/uploads/98fe36a5-9573-49af-b684-d8d4e8e769b8/alb-default-action.png)
A second listener is required for HTTP on port 443 so we can handle the secure traffic. First, you need a certificate to use which can be imported, from ACM (AWS Certificate Manager), or via IAM. This second listener needs to forward traffic to Tomcat. We'll use port 8443 to handle that secure traffic in Tomcat, so we need an action that redirects traffic from 443 to 8443.
#### Certificate
We need to add a cert to the ALB now so we are secure all the way down. You can import an existing certificate to AWS Certificate Manager and use that, or have AWS handle it and create one there.
One little mistake I made was directly copying the validation CNAME record from the ACM page to GoDaddy. You need to add the CNAME record with out the domain at the end; take off the ```example.com``` part! I wasted at least a day and lots of time with a support person.

---
The last step is to update your DNS from your original record (A or CNAME) to a CNAME that points to the load balancer's DNS. You don't have the IP, but the DNS does not change during the life of the load balancer, so we can count on it.

Now we have a secure active-active architecture that is secure to the load balancer as well as between the load balancer and the target instances!

![active active](https://silvrback.s3.amazonaws.com/uploads/d17d3fc3-0094-4ffb-a2b4-c019acc901a1/active-active.png)

# 🐾

Help along the way:
https://www.wissel.net/blog/2018/03/letsencrypt-java-keystore.html
https://certbot.eff.org/docs/using.html
https://medium.com/@raupach/how-to-install-lets-encrypt-with-tomcat-3db8a469e3d2