Why not? Ok, not really.

Unfamiliar with the other clouds and why I chose AWS over Google or Azure when building a Spring Boot app from scratch? I'll go into my reasoning below.

#### Popularity
The main reason why AWS is familiarity and popularity. It's true. Ever tried to search for an existing answer to your problem on the web for a mostly unused piece of software? I've done it a few times recently and it isn't fun. It can be nearly impossible to find your answer. The popular languages/frameworks/plugins/apps have loads of content written about them and for them, which means your probably has likely been found and solved by some one else already.

#### Developer Friendliness
As humans, it may not be the best platform to use. The console GUI has a few things left to be desired. The documentation (although now open source, so you can fix it!) isn't the most readable or understandable prose. BUT, the CLI is incredibly robust, the platform is extremely flexible, and the resources out there are incredible (though scattered), and finally there are multiple conferences. All devs want to go to conferences for one reason or another.

#### Maturity
AWS has been around for a LOOOOOONG time. They've seen it all and likely added every feature you will need, especially just starting out. They have the most availability zones (which is what matters - Azure's regions don't translate to AWS's regions), and thus the best availability for your app. They were first with a serverless platform and still lead that industry, but others are now catching up. Maturity also leads to the most tooling around AWS. Whenever cloud tooling is written they almost always start with AWS.

These main areas are what I'm choosing AWS for a first app, but it also means most people running Spring Boot these days are probably running it in AWS.

I also want to point people in the best direction if they are just starting. AWS is that direction, at least in the long run. Sure, starting out with one of the midtier providers like Digital Ocean is probably simpler (never used it for a monolithic app), but AWS skills have a lot more value in the market.

Anyway, I hope that provides some insight into my decisions and some scope around the Spring Boot app building series here.

# 🐾