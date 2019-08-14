Perhaps you're asking "So, what is Project Lombok and why did you add it in the project setup?" If so, good question!

Project Lombok is a library that makes it easy to create immutable objects. I'll try to quickly and easily explain the value of immutability while coding.

### Immutability

Immutable means that it can't be changed. The major reason this is valuable whne coding is that your code can focus on one (or a few) possibilities.

#### To the Post Office

Imagine you send a package using the post office (I'm using USPS as a reference here, but I'm sure most post offices globally work similarly), and abide by certain rules. Rules like you can't ship explosives, guns, flammable liquids, etc. You package up the item (the object) and send it off.

The package is handed off from the origin post office, to a postal carrier, to a large truck. Now, when it is in the large truck. there is some one riding with it who opens it, adds something to the package (changes the object) and it continues on the journey.

Now no one can be sure what's in that package. Perhaps there's something illegal in there. Maybe it is a teddy bear. Nobody knows. When the destination post office and the recepient (processing code) get the package (object), it can't be sure what to expect. That would not be a fun time: never knowing what could be in your package when you receive it.

This is the same as mutable objects in code. When an object is passed through different pieces of code, they can easily change mutable objects. The next downstream method or function has no awareness of what to expect and must expect anything and everything. It makes testing and coding more difficult.

#### Concurrency

Imagine that we're sending a letter through the post office, but we want it to go to multiple people. This is obviously not a real scenario, but let's continue with the example anyway - I can't think of a better one at the moment.

When each recipient looks at the letter (within moments of one another), we want them to see the same contents. If you object can be changed during the journey, we don't know what each of the recpient sees. They could be different...they could be the same.

This exemplifies the real problem with mutability. You just never know what you'll get.

### Solution

Immutable objects is the way to deal with this problem. When an object is created, it can never be changed. You must create a new one to make an object of the same type with different contents.

Project Lombok is a quick and easy way to do this using annotations.

#### Annotations

In Java, you can add annotations to your code in many places. It is what people like to call "syntactic sugar", which basically means it makes the code easier for human consuption. In this case, annotations are elements that start with the @ symbol and are immediately before the object or method you want it to affect. An example below will make it solidify in your head.

#### Example

Here's what I mean, a do nothing class, Dummy, that is tagged with a Project Lombok annotation, @Data:

<iframe src="https://player.vimeo.com/video/351975898" width="640" height="327" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

It doesn't look like it does anything. BUT, if we build the project and inspect the ```build``` folder, we find the compiled ```Dummy``` class. It has more code than we wrote:

![Dummy.class](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/005-image-001.png)

Now, if we add some elements to the class, we can see immutability in action here:

![Dummy.java](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/005-image-002.png)

Looking at the compiled class again, with the updated element:

![Dummy.class](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/005-image-003.png)

It is immutable because he only way to set ```foo``` on this object is in the constructor arguments. This keeps us from unintentially sabotaging ourselves in the future. We make this immutable becase we know we don't want it to change, signalling to our future selves not to change it. We can't.

### Tooling

When you first start this project we're building, you probably will get an error message that looks like this:

<iframe src="https://player.vimeo.com/video/351973538" width="640" height="163" frameborder="0" allow="autoplay; fullscreen" allowfullscreen></iframe>

Fixing it is as simple as clicking the link in the message and ticking a box:

![Annotation Processing](https://squarespace-blog-images-us-west-2.s3-us-west-2.amazonaws.com/005-image-004.png)

Now when you want to leverage the automatically generated code we saw earlier, Intellij will be aware of it.

Next time we venture into AWS for the first time - exciting!

# 🐾