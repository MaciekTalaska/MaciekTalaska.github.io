title: 'Wrocloverb 2017: Elixir vs Ruby - unanswered questions'
date: 2017-03-25 23:43:34
category:
- get-noticed-2017
tags:
- Wrocloverb
- Elixir
- Erlang
- functional programming
---

As promised in the last blog post - I am trying to answer some of the questions that were asked by the Ruby community during the 'Wrocloverb 2017' conference, and we're supposed to be asked during the 'Ruby vs Elixir' discussion panel. Sadly the panel was too short to have all the questions answered. 

### Wrocloverb 2017: Ruby vs Elixir discussion panel (unanswered questions) 

##### Q: Is it a good time to make a jump from Ruby to Elixir?

A: It is definitely a great time to make yourself more familiar with one of functional languages. With more and more cores packed into a single chip it becomes important to run tasks in parallel, and this is much easier to achieve when there is no shared state. 
As for the Elixir itself - recently a new version of Elixir has been shipped (1.4) and the language itself seems to be mature. Community is growing, there are companies hiring people who know Elixir - all that to me is a sign that yes, it is a good time to make a jump into Elixir. 


##### Q: What could be the negative consequences of switching from Ruby to Elixir? ;)

A: It may happen that similarly to others you will end up switching to Elixir for good - bad that's not necessarily a bad thing, right? :-)

You may lack some of the tooling or gems you're used to. Elixir + Phoenix is not as mature as RoR, so not that many packages are available. Community is smaller. You may not find exact replacement for some of the gems, or what you'll find will not cover all the use cases. It may take you some time to be productive with Phoenix and delivering your first Elixir+Phoenix app could take more than doing the same in RoR - but that's only due to the fact that it is going to be brand new to you, the same would be true if you wanted to switch from Elixir + Phoenix to RoR. 



##### Q: When refactoring existing RoR app to Elixir, which part of the app would you recommend to start with?

A: The question is why refactor working app? If this is due to performance related problems - the obvious is that what is bottleneck should be refactored first. 

But rewriting whole application using different platform is always a big task. To properly utilize Elixir's advantages it could be important to rethink how things work and rearchitect some parts of the application. This is especially important if we want to achieve higher level of fault tolerance. 

Sadly, there is no silver bullet for that, as each application is different and each app has unique set of its own problems. 


##### Q: What would be the good and bad use case for using `mnesia`?

Mnesia faq should help: http://erlang.org/faq/mnesia.html if you decide to go with mnesia you could be interested in 'amnesia' a mnesia wrapper for Elixir: https://github.com/meh/amnesia 



##### Q: What projects is Elixir good for?

A: If you need scaling, fault tolerance - Elixir is a good fit. The types of projects that could benefit from Elixir are:
- web servers
- backends (servers) of different kind, especially if the whole system is designed as distributed 
- chat server backends (LiveChat or WhatsApp are great examples how well these technologies fit) 
- all the systems that require extra stability / fault tolerance 


##### Q: Are there any performance hiccups/overheads related to (erlang's) garbage collector (e.g. how does elixir GC compare to `stop the world` problem in java)?

A: Yes, Erlang's virtual machine is running garbage collector but it works differently than the one you will find in JVM or. Net. First of all - Erlang applications may have very many (literally thousands) of heaps. All those heaps are being garbage collected independently. You may find more info on that under the following link: http://evanmiller.org/why-i-program-in-erlang.html



##### Q: Are there any good libraries for interacting with relational databases? (if so - which would you suggest?)

I may suggest to use Ecto (https://github.com/elixir-ecto/ecto) created by Plataformatec (the company that Jose Valim - creator of Elixir - works for). 

If ecto doesn't seem like a good choice for yourself - try one of the libraries listed in the 'ORM and datamapping' section under the awesome Elixir repository: https://github.com/h4cc/awesome-elixir/


##### Q: Why Elixir is “sold” to us as “new better Ruby” while its underlying principles are totally different? Won’t it result in Elixir programmers that do not understand Elixir (like Rails programmers that do not know Ruby)?

A: Elixir is *not* a better Ruby. The only thing that these two languages share to some extent is syntax. Please mind that even in this area there are significant differences. Elixir us functional programming language, while Ruby is not. That is a huge thing, and has enormous impact on how applications are developed. 

Elixir + Phoenix is not even remotely similar to the relation of Rails and Ruby. It is not something uncommon that even technical people say 'Ruby application' while they actually think of RoR application. Rails is extremely important for the Ruby world, and I will risk the thesis that without Rails (or similar framework) Ruby would be nowhere near as popular as it is right now. 
Ruby's niche is web application development. Period. Yes, it is used sometimes as purely scripting language (OpenSuse's YaST), there are also libraries which allow crating desktop apps using Ruby, but those are not areas in which Ruby shines and is popular.

Elixir is a whole lot different story. Elixir is not that specialized as Ruby. Apart from being most frequently used for backend development, there is no special niche that is most suitable for Elixir (which is a bit different for Ruby as Rails and web application development is extremely important in Ruby world). The only good advice is: if you are planning to write a server of any type - Elixir could be a great fit for that (even though it doesn't necessarily has to be a web server). 

Unfortunately there is a sad trend of not knowing good enough the technology that one uses - but that's no specific to Rails or any other technology. Some frontend developers don't know Javascript well enough.

##### Q: Are there any hardware-interaction Elixir libs or patterns that would potentially open a path for Elixir to IoT world - wouldn't rails be better for a deployment on a smart watch?:)

A: one of the projects aiming at the IoT area / embedded systems is nerves: http://nerves-project.org/ - have a look at the introductory video into nerves from Elixir Daze conference: https://m.youtube.com/watch?index=8&list=PLE7tQUdRKcyZV6tCYvrBLOGoyxUf7s9RT&v=TjlbXQ88eEc

There is a 2-part article on building IoT using Elixir: 
- https://monterail.com/blog/2016/iot-with-elixir-and-coap-part-1-example-on-how-to-easily-prototype-and-build-an-iot-platform
- https://monterail.com/blog/2016/iot-with-elixir-and-coap-part-2-example-on-how-to-easily-prototype-and-build-an-iot-platform

Of course Elixir - due to the way it can handle large number of incoming connections - is an excellent choice if you plan to build the server part for the IoT solution. 


##### Q: Is there a huge difference between tools available for Elixir and Ruby (IDEs, plugins, etc.)?

A: I would say that Elixir has almost as good support as Ruby. There are plug-ins for Atom, Visual Studio Code, Vim, Emacs, IntelliJ - and these are only the editors / IDEs that I'be tried on my own. 

There are a lot less packages available. Same as some tools (but on the other hand Erlang / Elixir offer some unique tooling that is not available for any other platform / language). 

Don't be afraid, Elixir is us not a language which appeared 6 months ago. It is suitable for production ready systems. 


##### Q: Should new comers start with Elixir or Ruby? As most of the talk today that happens is about scaleable, high throughput web apps. Is scaling relevant to everyone?

A: You forgot about fault tolerance :-) 
No, not everyone needs scaling. That's true. But it is also true that you don't have to design application in such a way that it becomes fault tolerant and scalable. It doesn't come for free with Elixir. If you don't need it - you don't have to overcomplicate things. You could built simple web application using Elixir + Phoenix as well as using Ruby on Rails. 

The last difference would be functional programming vs OOP. Some say that fp is harder to learn than OOP. That is not necessarily true. Have a look at http://haskellbook.org - this book has been co-authored by person who was taught Haskell as her first programming language. What's more - she has started teaching Haskell her 10 year old son :-)

So back to the question - I think that it is the best moment to get submerged in the world of functional programming, and Elixir is one of the most interesting languages (with very bright future when it comes to jobs availability) to be used for learning fp. Go get it, and start some fun using it! 


##### Q: What applications or common problems are not good fit for Elixir? So if we have multiple micro-services should be kept in Ruby?

A: Even though Elixir is a general purpose programming language it is not the best fit for every type of application. 

I am not sure how well would it perform on extremely small devices, devices having only 16KB of memory and a very weak cpu. On the other hand Elixir plays well on RaspberryPi, BeagleBone and Chip (the "world's first $9 computer" - as it is advertised). 

One of the field that is not the Elixir niche is game programming. The other would be numerical computations - why compete with R or Python - both languages are de facto standards for data scientists. I wouldn't Recommend Elixir / Erlang to cope with CPU intensive tasks such as number crunching which may require a lot of processing power. 

Elixir could be used instead of Python for system scripting, but I don't think it is a good idea. Python is usually part of every Linux distribution, and Erlang and Elixir are not... 

I am not sure how well Elixir copes with desktop application programming, but I would probably go with something else. 

I wouldn't use Elixir to write some system extensions (kernel modules, drivers etc). 


##### Q: Is Phoenix going into Rails direction and will it suck in like 5 years?

A: Hard to predict what happens in 5 years time. Big percentage of converts to Elixir have background in Rails - it is possible that Phoenix will not be shaped as 'Rails for Elixir' but rather a framework that is just inspired by Rails. That is actually happening right now in the Elixir community. Instead of just copying solutions z community is trying to find the best approach for solving particular problems. 

Neither Elixir nor Phoenix are perfect. I am sure than in 5 years time there will be some things to argue about, I am sure there will be approach to create another framework that would be considered alternative for Phoenix. Thesw are all things that will happen for sure. I just hope there will be very few people saying that 'Phoenix sucks'. 


##### Q: What are the bad parts of Erlang / Elixir?

A: It is going to be się making different for each and every developer. For me personally there are couple of things that I could call disadvantages:
- raw processing speed - if you're in need for CPU cycles you will probably have to think of some other language (Rust?) 
- Elixir NIF (Native Implemented Function) these are usually written in pure C and consumable from within Elixir. Everything would be cool if not the fact that poorly implemented NIF could bring the whole Erlang / Elixir virtual machine down. This could be pretty surprising for someone who learnt that in Erlang / Elixir processes could be 'resurrected' thanks to supervisors, so failing process should not be a problem.
- Erlang is very mature, but Elixir is still quite young, and that means there are not as many libraries as for example NodeJS packages, Python eggs or Ruby gems. 


##### Q: How many of your past projects would fit more to use elixir instead of ruby?

A: I had a chance to write software for the biggest companies operating in the financial area. I am pretty much sure that couple of systems I have helped to create could greatly benefit from rewriting in Elixir. 

At some point of my career I had a task to design an architecture and develop a game server. At that time I have decide to use Python + Tornado, but today I would probably go with Elixir. 

The RoR apps I have created were quite simple and didn't have any sophisticated requirements. I could rewrite them in Elixir but without any architectural changes there would be no gain from that. If I was already an Elixir + Phoenix expert I would probably choose Elixir anyway, I even for the very simple, classic web applications. Why? Why not? :-) there is no disadvantage of choosing Elixir - no extra appetite for resources etc. 

Only one drawback could be with hosting - RoR is by far more popular than Elixir+Phoenix so it could be more tricky to find a good hosting for apps written in Elixir. 


##### Q: If I would want to create a chat app, why would I want to use Elixir instead of Node?

A: It all depends. Have you heard of LiveChat (https://www.livechatsoftware.pl/)? They are offering chat capabilities as a service, and are inexpensive if they biggest companies of that kind worldwide. They have made a decision to rewrite their backend (originally in C++) in Erlang. Why? They wanted something reliable and still well performing. 

I have tried to crate small chat applications using JavaScript based technologies and from my experience the best fit for that was MeteorJS. 

Why Elixir and not NodeJS? Mainly because it possible to guarantee fault tolerance when using Elixir. Scaling would also be easier to achieve. The question is if this is something that is required by chat application. It is a different situation when a chat is a tool for client facing marketing, and different of this is just a platform to exchange picture of kittens :-)

Oh, and please mind that WhatsApp has its backend written in Erlang B-)

### End note 
I have tried to be objective as much as I could, but I am an enthusiast of Elixir and fp. Some time ago I was actually thinking of getting into the RoR world as my primary technology, but after discovering Elixir I started having doubts and... decided to actually concentrate on Elixir and Phoenix.
