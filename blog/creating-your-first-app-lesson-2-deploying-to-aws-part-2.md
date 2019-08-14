Today we're wrapping up our first deploy to AWS. I already gave some backstory to what we're doing, so let's just get it done!

Follow along below with the written instructions.

<iframe src="https://player.vimeo.com/video/352401807" width="640" height="550" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

0. Pick your favorite flavor of Linux. I like Amazon Linux because they also install some helper software related to other AWS services
0. Choose ```t2.micro``` because that will be free for those of us using new accounts
0. Leave many settings default
0. Turn on termination protection (good practice for instances you want to live for a while)
0. Leave storage default
0. No tags needed (unless you want to add some)
0. Create a new security group and leave it default
0. Click Launch and choose to create a new key pair - name it what you want and click Launch Instance (downloads the key)
0. Make sure you keep that certificate file safe. YOU NEED IT TO CONNECT WITH THE INSTANCE.

### Server Updates

There are a couple things we need to do on the server to access the app. First, we need NGINX. I'm going to simplify things here and refer to NGINX as only server software, which isn't quite correct, but that's basically how we're going to use it here.

Installing NGINX on Amazon Linux 2 is quick and painless - just SSH into the instance and run a few commands.

<iframe src="https://player.vimeo.com/video/352405073" width="640" height="480" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

Now, we need to adjust some security settings in what AWS calls a Security Group. We created one when we made the instance, but now we need a new permission to allow communication to the server and app from the outside world.

[Update SG]

### Take a Look

Now we can navigate in our browsers to the app and view it. Copy the public DNS from the AWS console and paste it into your browser. Voila! Ok, not much to look at, but small iterations are key when building software and making progress.

Next time, we'll automate this so we don't have to do this every time we want to make a change!