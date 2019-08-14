After touching on the term monolith, in the context of software engineering and design, it seems necessary to dig a little deeper into the term and some reasons how it got to have such a negative connotation in recent times.

I’m going to use my personal experience to relate and tell the story of where we once were to where we are now and how we got here…related to monoliths anyway.

My first job in the software industry was manually testing Windows Media Player in the soon to be released Windows Vista operating system, circa 2006. Windows then (and now) was a big installed piece of software that had everything from GUI (graphical user interface) down to hardware drivers. Not sure it was ever referred to this way at the time, but it was a monolith. Windows Media Player was very similar because everything it did was encapsulated in one installable piece of software.

Were these two pieces of software poorly designed? Ok, well, maybe they had some problems that were fixed down the line and maybe you don’t agree with how it was designed. BUT, was (and is there now) a better way to design these pieces of software? No. To use a desktop/laptop computer, you need an installed operating system with all parts intertwined and depending on each other. A loosely coupled operating system will not work. A desktop media software needs to have lots of functions to give it value, especially in its time. We, the customers, expected it to do everything. It had to be a monolith.

I can continue to give examples throughout my work history where a monolith was the right decision.

Zune. How else can you run software on a mobile device?

Windows Phone. Ditto.

Kelley Blue Book mobile apps. This one blurs the lines a little because apps generally use APIs on a server elsewhere to power them, but the app is one big packaged software deployable. Monolithic-ish.

DirecTV set-top box apps. Ditto.

At this point in my career, I started working with web apps. Here is where distributed software and microservices get thier day in the sun.

Diverging for a moment, I want to discuss the major downside of monolithic software and how microservices solves it.

Working as a large team on a monolithic software project is very complicated and difficult. Trying to get changes from tens, hundreds, or even thousands of engineers merged and tested is a very difficult feat. However, if you are able to break up that big piece of software into much smaller pieces that live by themselves, then the teams don’t need to be much bigger than ten. It becomes miles easier to contribute to a project when the entire team can fit in a small room. Communication is easier, changes don’t clash as often, and the entire system can be relatively easily reasoned by each engineer. In other words, a single engineer can know about and change any piece of the software.

Changes, from the idea to a shipped product, used to take at least months, if not years. We needed that time to coordinate and push all the changes through…and to test. You don’t get too many shots to make bug fixes when it is so costly to update the software.

Microservices solves all that by splitting the software up into chunks that smaller teams can develop. This allows for quicker communication, smaller features, which leads to smaller changes, and more deployments. Communication is much easier with smaller teams because there are fewer people to interact with. The conversations goes up exponentially with the number of people on a team. If you cut up an application into small pieces, the features become smaller because your overall scope is already smaller. You deploy more often because you don't have to wait for gigantic merges or large features to complete. Technology also helps with this front; being able to deploy quickly has been improved over the years by the tools and computing in general.

Back to my history as a guide...

When I started working with webapps at Nike in 2013, we were just scratching the surface of continuous deployment and microservices. Our software was cut up into major chunks, yes, but we still deployed on a what was essentially a huge monolithic website. Contrast that with the SaaS I'm working on now: we deploy each service independently and can do so within a matter of minutes, no matter what is going on with the other services.

Basically the above reference encapsulates my entire work history at Nike. Unfortunately, I wasn't able to escape the software life of a monolith living alongside everyone else. But, that's a relic and an uncommon one these days. Not all monoliths are the same.

Now, up to the current era, back to my current SaaS work. We have multiple Spring Boot apps that all live in the same server, and they are all monoliths. From a technology perspective, everything runs fast, is easy to develop in and change, and is quick to deploy. Monolith FTW!

I hope this gives some perspective into the (or at least my) history of monoliths and why they shouldn't get a bad rap.

# 🐾