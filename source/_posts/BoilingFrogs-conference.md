title: Boiling Frogs conference
date: 2016-01-21 07:03:20
tags: 
- Boiling Frogs
category: conference
---

Last Saturday (16th of January) I had a chance to take part in the Boiling Frogs 2016 conference. This is not very widely known event - at least I haven't heard of it before my friend told me couple of weeks ago. Boiling Frogs is organized in Wroclaw, Poland. As far as I remember this year's edition was ~~the second one~~ (actually I was corrected on that: this was the first edition of the conference). What is interesting is that there is no huge company behind organizers. You may actually say that Boiling Frogs is a community driven event is oranized by people who form community.

I was quite surprised that this event offered three separate tracks of talks. I understand how much of an effort is required to prepare even a single track conference, but three separate tracks... well done Boiling Frogs 2016 organinzers! Each track had a mixture of talks: some focused on very technical aspects of software development, some others more focused on a topics that focus on software from a bit higher perspective (architecture, project management etc.).
One important thing to note was that even though most of the presenters had their slides in English, talks were held in Polish only (at least all those that I have attended).

### Opening Talk

Conference started with opening talk by the main organizer: Tomasz Kaczmarzyk. Tomasz told us about the history of the conference, the effort himself, team and friends and family devoted to make this event happened.

### Talk #1 - "From legacy to DDD"

After the opening talk I decided to listen to Andrzej Krzywda (from Arkency) talking about his journey from "Legacy to DDD". That was a very interesting talk. Andrzej told us a bit of his effort to find the architecture/approach that would help him build software that is most valuable to his customers. It was great to hear how an adoption of some techniques enables developers to think more in terms of business opportunities than in strictly technical manner. Some time ago I was told that pure technical excelency is not that important as being capable of delivering technical solutions, but in the same time understanding business and being able to suggest new features and functionalities. 
Slide deck from Andrzej's talk is available online: http://www.slideshare.net/andrzejkrzywda/from-legacy-to-ddd-5-starting-steps
The most important things to take from the talk:
1. Learn ideal DDD - to think about implementing any (part of) system in DDD you should learn the most important concepts first. Obvious, right? :)
2. Publish events (just in case to be ready to later make further changes to the application code, and benefit from 'just publishing events')
3. Microservices are hot. What they bring on board is requirement to have things done in an async way. The question is: do you and your team have enough knowledge and experience to have it done on your own?
4. Frameworks are great, but... sometimes you end up being a prisoner of the framework of your choice. It is a good idea to separate framework(s) from the core of your application. Why would framework specific objects leak into the most inner part of your application? Andrzej put a lot of emphgasis on separating network (http) and storage/database layer from the application.
5. Learn bounded contexts - this is actually the core of your project. It is the most important to have as good understanding of it as possible, that's why you should think of how to model your 'world'.

I personally love talks like that one. This is the level of understanding how software works (or should be built) that I think is the most important. This kind of perspective requires not only ability to code, not only knowledge of frameworks, but moreover knowledge of some architectural approaches and (maybe most important) experience: a lot of hours 'wasted' staring at the code and thinking how to improve that. 

### Talk #2 - "BDD and agile requirements"

The very next talk that I have attended was entitled "BDD and agile requirements", given by Wiktor Żołnowski. Wiktor is experienced QA and consulant, who helps many companies make sure that the software they create is of acceptable quality.
This talk was packed with a lot of stuff:
- proper approach to define BDD scenarios
- introduction to GROW (Goal, Reality, Opportunites, Work) approach
- a story of a startup that Wiktor has been advising
- introduction to usage of Cynefin (have you *ever* heard of it before reading it here? no? google it!)

It is easy to spot that Wiktor has a lot of experience in advising companies and organizing how teams work. Great talk.


### Talk #3 - "Paradise for polyglots - everything floats"

Right before the lunch I have attended interesting talk by Michał Płachta "Paradise for polyglots - everything floats". This one was aimed at reactive progamming. Michał was showing the audience how to build a simple snake game using reactive approach (so approach based on streams). From the very simple thing (snake and fruit in the same place all the time), Michał went to a full featured version of the game. Just to show that reactive approach could be used on both: frontend and backend (same time) - Michał got to the point of having two different players (snakes) at the same time. Snakes were synced using backend (written in Scala+Akka). It was really impressive talk. I was really inspired by the way such a simple application has been built with the reactive concept in mind. 

### Lunch

The lunch was a great opportunity for myself to talk to couple of my colleagues, and to eat some pierogi :) (if you have ever visited Poland, you have surely been offered pierogi, no doubt!). 
Great time to have another look at the agenda and mark talks that seemed the most interesting.

### Talk #4 - "Effective Software Delivery"

First talk after the lunch that I heard was "Effective Software Delivery" by Jakub Kubryński. Jakub cooperates with Bottega Solutions, and I must say, that I have heard couple of talks by people who work for Bottega, and each time it was time well spent. To me this is now clear - presenter who works for Bottega = high quality of the talk.
Back to the talk: Jakub was talking about all the different approaches we take to make sure we can deliver software of high quality. Jakub has also pointed out couple of different approaches that are quite common but result in the development of software of not-so-high quality.
One of them was hacking models/database - using columns or properties to enable some additional features: "during this transaction we don't use the property X, so if this is set to Y...". Does that sound familiar? Another one: "yes, I agree with you - I'd like to have this feature tested, but trust me, this one is special and you can't test it". Scripting? "I know it should be automated, but...".
Another thing that was touched by Jakub: what is the difference between PoC and spike(s)? When should you go with PoC? How do you evaluate technology? Should you trust something just because it prooved useful in a previous project you worked on?
Another interesting thing that Jakub touched was the way we build software in general, how we think about it. Is architect a good name for someone who is in charge of technical side of software development? Is building houses really good analogy? 
Apart from that there were couple of other things mentioned: silverbullets (in terms of technology), praising small changes, knowledge of your tools, scripting and automation of tasks, testing software, DRY (and WET), premature optimization, code inspections and couple of more. For experienced developers some (all?) of the things mentioned should be familiar, but still it was a great summary of techniques to make great quality apps. For not that experienced developers this should be one of the required talks.

### Talk #5 - "How to find time for quality? Theory of queues and Little law's in the software development process"

The very next talk I went to was another one given by Wiktor Żołnowski: "How to find time for quality? Theory of queues and Little law's in the software development process". Originally I wanted to go to my friend's (Tomasz Pluskiewicz) talk "HATEOS as if you meant it", but I decided that the previous talk Wiktor gave was so good, and that I have already talked to Tomasz couple of times about HATEOAS that... I have decided to go for the second talk given by Wiktor. His talk started with a simple problem: how to optimize a system. We were thinking about McD-alike "drive-in" system, which  has 3 different stages: placing order, payment and order collection. The trick was that each stage took a different time to be completed. Wiktor has shown couple of simulations using different number of vehicles being in the queue. It was interesting to see that squeezing too much actually makes the whole system performing much worse than we would expect. 
Taking it from there Wiktor elaborated more about how to improve performance of a team that uses Scrum. He pointed couple of things to consider that are related to work organiation, amount of work planned to be done within a sprint etc.
I think that both talks by Wiktor should be attended by all managers in IT. I agree with Wiktor: we do lack managers in IT who have management background (as the common story is that developers are being given a chance to manage and they do it as well as they can). 

### Talk #6 - "Machine Learning for Developers"

The very last talk that I have attended was "Machine Learning for Developers" by Mariusz Gil. I am not sure, but this may have been the most important talk of all for myself. Why? Simple reason: I had no idea what machine learning was, before entering the room where the talk was given. After ~45 minutes I am still no expert in the area, but at least I have an understanding what machine learning is, where could it (possibly) be applied and what are the things the you should consider when building a machine learning system.

After the conference we have headed to the pub where we had a bit of a disussion on IT, software etc. I came home quite exhausted, but happy, as I considered this day to be a well spent one. I have learned some things, I had a chance to talk to some of my colleagues I know from local tech groups, and make some new acquaintances.

### Summary

As for the confenece itself I must say that I like these type of events: organized by smaller group of people. Made with passion and not because there is a business aim, or an opportunity for a company to make its brand better known.
Boiling Frogs was one of the events that boost you with energy, that makes you become better in what you do on a daily basis. 
If there is another Boiling Frogs conference next year to be organized - I will definitely make sure to get a chance to attend it.

I think that 2016 has started very well. I can't wait for other opportunities for me to develop my knowledge and attend even more interesting events.
