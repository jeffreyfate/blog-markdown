##### Hi! 👋 My name is Jeffrey Fate. I've spent my entire career ensuring and creating quality code. There have been many roles in my history: manual quality assurance, automated test developer, full stack engineer, devops engineer. In all of the roles I've taken on, my mantra has always been the same: Quality Counts. I'm going to do my best in sharing how to develop software from that lens, starting here...

### Coding Can Wait (or how I stopped worrying and learned to love FDD)

Only recently did I discover the three letter acronym FDD. I already knew TDD (more on that later), but hadn't heard of FDD. It made intuitive sense though. Feature Driven Development is probably writing software from a feature mindset. If the following sounds familiar, it closely relates to domain driven design (DDD).

#### FDD Creates Quality Code

Coming from me, this has to be the angle. I'll explain how we get there by describing the FDD activities and best practices.

##### Model First

Coding first feels right - to get something working - but taking an overall look at what the goal is, it becomes more clear and quicker to develop it.

  0. Overall Model
     - Break into groups (or as individuals) and come up with the model of each domain then come together and select the model for each
  0. Feature List
     - Further decompose the domains by developing features in each area. Each consists of client value in the form of: ACTION RESULT OBJECT. Example: "Send reminder email to user"
  0. Individual Features
     - Plan development for each feature by splitting up the features and writing up cards to be worked on independent of each other
  0. Feature Design
     - A developer (or group of developers) documentation is written describing (and diagramming) each feature. These plans are peer reviewed prior to cutting code.
  0. Build Each Feature
     - With planning done, each feature can be coded and tested independently.

I'll be the first to say, all of these steps might be overkill for a lot of work we do on a daily basis. BUT, if you keep the general idea of this process in mind, the goal can be achieved repeatedly: develop the feature first, then start coding. It reduces the position of being stuck between code and a hard place after half completing features only to realize the design in your head isn't complete. Been there!

If you'd like to hear my spout my mouth off (as opposed to my keyboard) about feature design and coding later, check out my podcast [Discode](https://discode.dev). You can find it on any podcast aggregator like iTunes and PocketCasts.

#### Best Practices

Just a few common practices not already covered above.

##### Reviews and Visibility

##### Collaboration

##### Communication

Helps eliminate bad ideas or partially complete features

Following FDD helps you write better code