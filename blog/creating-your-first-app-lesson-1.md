I’ve recently realized I have a bit of experience in Spring and monolithic applications generally, but have never built a Spring Boot app from scratch. Time to de-bucket that bucket list item!

To make sure we’re all on the same page, these are my prerequisites:

- Intellij IDEA Ultimate (unfortunately the Community Edition doesn’t really support Spring Boot)
- AWS (my cloud of choice)
- MacOS (more specifically, a MacBook Pro circa late 2016)
- Java 12 (because sometimes the bleeding edge is actually not that bloody)

Using Intellij makes the creation of the app almost too easy. It has an integration with Spring Initializr that allows you to create the type of Spring app you want with the dependencies you want in a snap.

The first step is to create a new project from the Intellij welcome screen. Close any other Intellij windows you have open and you should see this:

![Intellij welcome screen](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/001-image-00.png)

Gently tap that `Create New Project` button and choose Spring Assistant on the next screen.

![Spring Assistant](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/001-image-01.png)

Notice I have Java 12 already installed. If you don’t, see [this post]() on using SDKMan to do so.

Choose the default and then Next.

![Project Properties](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/001-image-02.png)

Above are the properties I’m starting with. Change your Group Id to something unique as well as Package name and fill in the rest. Hit that Next button.

This is where we need to know what type of app we want. We're building a web app that is a monolith. That means we want everything from the web front end, to the services backend, to the database in the same codebase.

The first section, Developer Tools has only three items and we want them all. We also want the latest stable Spring Boot version, which is 2.1.6 at the time of writing.

![Developer Tools](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/001-image-03.png)

In the Web portion, we want Spring Web Starter and that’s all for now.

That’s all we need for the basics. Click Next.

Decide where you want to store your project and click Finish.

![Finish](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/001-image-04.png)

You’ll now have your main Intellij window with an import window on top. Just match what I have (leave the Gralde project path alone) for the settings here and we’ll hit OK. (It’s fine if the Gradle home and Gradle JVM paths don’t match mine, we’ll deal with some of the other setup after this).

![Import Screen](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/001-image-05.png)

Now you’ll see Intellij is doing some work. The Panel should appear that looks something like this:

![Build Panel](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/001-image-06.png)

Wait for that to finish. If something fails, leave a comment below and we can solve it together. I’ve seen so many errors at this step depending on how your system is configured, but I can’t capture every single one here.

Lastly, we want to make sure we’re all on the same Gradle version. Get the latest stable by visiting the [Gradle releases page](https://gradle.org/releases/) and noting the latest version number. In my case it is v5.5.1. This is what the releases page looks like as of this writing:

![Gradle Releases](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/001-image-07.png)

Back in Intellij, find the `gradle` folder in the Project panel (usually on the left), expand it, then expand `wrapper` within it, and double-click on gradle-wrapper.properties. Here we’ll edit the `distributionUrl` to point to the version number above:

![gradle-wrapper.properties](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/001-image-08.png)

Once it is changed

![Version Update](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/001-image-09.png)

Save (CMD+S) the file and Intellij will build automatically again.

That’s it!

Ok, that turned out to be a lot more writing than it is action in Intellij, but I want to make sure we are all on the same page from the beginning.

Come back tomorrow for the continuing saga in building a Spring Boot monolith from scratch! (I’ll address the bad connotations some people have with the word ‘monolith’ in an upcoming post).

# 🐾