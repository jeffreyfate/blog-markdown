Next we're going to deploy this do-nothing app to AWS. This is an important step. Here's how I see it.

#### Gain Understanding

We're at a crucial moment where we're not bogged down by all the details of what the app is doing - like I said, it does nothing. We can focus on how it is deployed and gets to the rest of the world. We'll use this knowledge to make deploying it repeatable and eventually automated so we don't have to think about it any longer. BUT, we'll know how it all works so we can problem solve why deploying doesn't at soem point in the future. Yes, this will happen.

#### Understand Only a Few Pieces

It is much easier to gain understanding when we have such a simple app and there is nothing else to know about. All we need to know is our app and how it gets from our laptops (I suppose many folks still have desktops, sorry) to the cloud server. That's it.

## Let's Get Started

### Build It

First, we need to build the app into something that can be deployed. This is great because we're using Gradle, which has a simple way to do it. Run this command from your project's directory in a terminal of some kind: ```./gradlew clean build```

After a few seconds, the build completes and your deployable will be in ```$/build/libs```

(I'll go into further detail about Gradle and what's going on here in a future post)

Yay, we've got the app. Now what?

### AWS Land

If you don't already have an AWS account, get one. Head over to [their website](https://aws.amazon.com/) and click the big orange button in the upper right to sign up. The great thing about not having an account yet, is you'll be on the free tier for a year. AWS provides new accounts with some resources free for an entire year. We'll be leveraging those to make this free for anybody who wants to create a new account.

Now that we have one, we'll be getting familiar with their online console. Eventually we want to use the AWS CLI (command line interface), but for now we'll get to know the GUI on their website.

From the Console Home click the region selection in the upper right

![Console Home](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/006-image-001.png)

Choose Oregon (you can do whatever region makes sense to you, usually the closest one, but I'm going to do everything in Oregon)

![Oregon](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/006-image-002.png)

Now, still at the Console Home, click the Services menu

![Service Menu](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/006-image-003.png)

Choose EC2 (Elastic Compute Cloud)

![EC2](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/006-image-004.png)

From here, we're going to launch a new instance. This will be an abstraction of a computer. It has processing, memory, networking, and storage just like a computer. This is where our app will run.

Unfortunately, I've ran out of time for this one. We'll wrap this up next time. After all, we don't want to start up an instance and leave it running without getting our app deployed there. That would just be wasteful!

# 🐾