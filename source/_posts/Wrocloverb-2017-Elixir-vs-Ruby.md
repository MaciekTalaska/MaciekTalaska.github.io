title: 'Wrocloverb 2017: Elixir vs Ruby'
date: 2017-03-19 22:49:41
category:
- get-noticed-2017
tags:
- programming
- Elixir
- Erlang
- Ruby
- Rails
- functional programming
---

I had a chance to spent couple of hours on the annual Wrocloverb conference this weekend. One of the most anticipated events during the conference for myself was "Elixir Panel". I had high hopes for great, open discussion on the platform that seem to attract more and more people from Ruby community.

Unfortunately this was not that great as I expected. My biggest complaint was the bias, but let me start from the very beginning.

The panel itself was in the form of "experts have voice". There was very little involvement from the audience (apart from one person, who at some point joined experts, or should I rather say replaced Roberet. Unfortunately I do not recall this person's name). 

The "Elixir side" were two developers having background in Ruby (as well as in Elixir):
- Hubert Łępicki
- Michał Muskała

"Ruby side" was represented by two Ruby, Rails experts from Arkency (the company behind Wrocloverb):
- Andrzej Krzywda
- Robert Pankowiecki
First thing, and first bias: AFAIR neither Andrzej nor Robert have any hands on experience with Elixir. That means that on Elixir side there was good understanding of Ruby/Rails applications, but on the other hand - the "Ruby side" was very lacking in terms of 'What Elixir is' (saying that 'Elixir is Erlang based functional language' is just a simplification).

### Questions

It all started with scalability (which is a selling point for Elixir) and performance. At the moment Elixir seem to perform a bit better than classic Ruby (so not JRuby, or Ruby run using Graal + Truffle). There is a lot of effort to make Ruby perform better and better. What struck me was that a claim  that 'performance is not an issue'. Well, I think it is actually the opposite. In todays world it is quite common that app popularity may spark right out of the blue. App performance is important as it allows more clients (customers) to use the app the same time, and that makes cost of a single request cheaper. 

Discussion on scalability lasted for good 10-15 minutes. At some point I have heard a comment "what else is there in Elixir apart from scalability" ;)


1. Elixir community is not great.

To me that was really bold statement. Recently I have seen some talk from Elixir conference, and on one of the slides it was pictured where do people come from when migrating to Elixir. I am not sure about the exact number, but the vast majority of people come from Ruby+Rails. So... if Elixir community is not great, that would mean that... RoR community is not great :>>>

I would say that Erlang/Elixir community may be a bit different than Ruby's. I have the feeling that there are quite many Erlang developers who are twice as old as some of the Ruby devs. It may not be true that there are so many experienced users of Erlang, but I still have a feeling there are definitely more Erlang devs in their 50s than people of the same age in the Ruby community. Erlang has been around for 'a while', it is doing great again, inspires other languages - such as Elixir etc. I may suspect that some of the people being in their 50s or even 60s may behave a bit differently than people who are in their mid 20s. Does that automatically mean that Erlang developers are not friendly? I wouldn't say so - but personally I have a very little experience with Erlang community so far.
To sum up: yes, Erlang community may be a bit different, maybe not be that dynamic, but for sure is not hostile. Elixir's community is actually a lot similar to Ruby community, and from my experience it is extremely friendly.


2. `I have attended Erlang/Elixir meetup and they were talking for 1,5 hour about authentication. Hey, Elixir People! - Devise is already there in Ruby for years!`

Well... that's funny again. Erlang/OTP is very mature platform on top of which Elixir is built. Phoenix is a web framework for Elixir. Elixir and Phoenix are quite new comparing to Ruby+Rails. And that means that some of the concepts still has to be 'borrowed' from other languages/platforms. The same thing happened to Ruby - it took some time for Rails to emerge.


2. Apart from scalability why would I use Elixir?

From my perspective it could be just a matter of taste. If you're more into the functional programming paradigm - give Elixir a try. If you are interested in actor model, being able to write applications in a bit different way, make your application fault tolerant (or just want to learn how it works in Erlang, but Elixir's syntax is more appealing) - give Elixir a try.
Sometimes it is good just to try something different. You don't necessarily have to switch, but such an experience will definitely broaden your knowledge and make you a better developer.


3. Why use Elixir/Erlang with their actor model if I could use Akka + Scala/Java (nad JVM is less exotic than BEAM)
4. Why use Elixir/Erlang if we may have actors in Ruby?

Akka's and Erlang/Elixir's implementation of actors are a bit different from what I've read. It was alread pointed by Michał that there is some problems with actors being blocked sometimes when using Akka. This doesn't happen with Erlang/Elixir actors (process).
The other important thing worth noting is that actors (processes) and all the mechanisms used to maintain them are core part of Erlang/Elixir. This is different with Akka, as this is 'just' a library. There is no extra support for such a paradigm (actor model) into the JVM itself.
If someone wants just to try out the concept it is good enough to use the favorite programming language to play with actors. No need to switch to Elixir or Scala+Akka. Introducig actors could bring some benefits to your application(s), but if you expect extra stability and fault tolerance in your Ruby application just because you're using Ruby's implementation of actors (and there is no special support for this paradigm in Ruby VM) that will simply not happen.


4. Ecto+Phoenix are small in terms of LoC. Rails is big. In x years Phonix & Ecto will definitely grow.

Well, that may or may not be true. It all depends. Thinking this way would mean that Rails is (was) no better than other frameworks (as you can't keep your awesomeness thorough the years). I think that many people were using Rails for quite a long time, and right now some of them are helping make Ecto+Phoenix better. It doesn't mean that Ecto+Phoenix will be perfect, no - there will be definitely some things to argue about :) But what I personally think is that there is a chance to learn on experience of others. There is a chance that Ecto+Phoenix may actually improve in some areas in regards to Rails.


6. Tooling in Elixir? Is it mature?

It has been said that there are not many great editors/IDEs with support for Elixir. It has been also noted that this will be addressed during the summer 2017, as Microsoft invented protocol of interoperation between editor/IDE and Elixir will be implemented. 

Personally I encourage you to give Emacs/Spacemacs + Alchemist plugin a try. From all those editors that I have tried out already, this combo seems to be the most mature, and the most convenient. There are plugins for Atom, Visual Studio Code, Vim (these are the ones I tried out) and many other editors. There is also a plugin for IntelliJ if you prefer a full blown IDE instead of 'just an editor' - I haven't tried IntelliJ with Elixir plugin on my own.

It is always possible to have better tooling, so this is a bit of a 'neverending story' for us, developers. On the other hand it is worth mentioning that Erlang/Elixir provide some interesting tools - for example nice process monitor - which I believe may not be available on other platforms. So yes - tooling differs, but it changes for each and every platform (for better, of course!).


7. I have x years of experience in creating Rails apps. AFAIR there were just as little as y projects that could benefit from scalability (or better performance). 

Well that is actually quite simple - you just don't touch different niches when using Rails. The good example that were mentioned during the talk were: game servers, IoT. I do understand that each and every application may have a complex business logic, and this is what becomes the most important requirement - to have things coded in a way that makes business happy. Sometimes it does happens that there are also important non-functional requirements to be met. Some of these could actually be scalabilty or performance.

But... if you don't question your choices (some of them may have been made quite some time ago) so how do you progress? Why not just check what some other, hot, not-so-mature technolgies have to offer? What if there is really *something* out there? You may just be unaware how some other tech could improve your life as a developer. 


8. Success story: "thanks to Rails app could be shipped in a short time. Later as the cost of a request is high - that business needs to close. But at least we got our foot into the business..."

Is it a success story actually? Doesn't that make Rails an Ruby a PoC platform? A platform which is great for prototyping, but actually is not that great when it comes to running business depending on it? We're not all running such a big systems as Twitter or LinkedIn, but there are well known stories of migrating from RoR to other platforms and languages only due to the fact the those other technologies offered better performance (or scalability).
That question is really one that you can argue about for hours...


9. It is easier for people to become stars in Elixir community.

I dont really get this one. It was the same with Ruby/Rails 10 years ago. Each and every technology has its own 'immature' years, where many libraries are yet to be created (or simply need to mature).
The other thing is: if you realize that there are no (yet) developers who started their journey in software craftmanship with Elixir - does that mean that all we - Elixir lovers - are just attention seekers? ;) Does that mean that only 'weak' developers take the Elixir path - as it is so easy to become 'a star' in Elixir community?
Another thing - please note that one of the experts was Michał, who not only contribute to Ecto and a person who actually is in the middle of writing a book on Elixir. Taking all that under considertation - don't you think it was actually rude, as it was actually *argumentum ad personam*. This question made me somewhat... uncomfortable. I know that Michał didn't take it personally, but still, it was weird/strange question.


10. Elixir community is anti-Ruby...

Well, that strange, as I am following Elixir community for ~9 months right now, and haven't spotted such a hostile approach against any technology. Frankly speaking I felt that it was Ruby community on Wrocloverb who was... a bit anti-Elixir. This is what I found strange. I had the feeling (from previous attendances to this conference) that it was actually open to different approaches, languages and frameworks. It was the case with all the JS ecosystem (ClojureScript, React, many other technologies/frameworks), but the important thing to note here is that all the technologies warmly welcomed by Ruby community during Wrocloverb were actually technologies which could be easily consumed by Ruby developers to enhance their apps. There was no real Ruby competitor mentioned on the last 3 editions of Wrocloverb - or at least I don't remember such a situation. This is where Elixir differs in comparison with ReactJS - Elixir is not something one incorporates into Rails/Ruby app. Elixir is also not a language that most of the Ruby devs find appealing (even though its Ruby inspired syntax). But the biggest thing here is that it seems that Elixir community grasped a momentum, and there is a lot of hype on Elixir right now. I suspect that some of the Rubbyist feel that Ruby/Rails may not be as popular in the future as they are right now. But instead of learning more about 'the enemy' is it so wise to be anti-Elixir? ;)

### Summary

One thing that I didn't particularly like was the bias. It was not as objective as I could (should?) have been. The strange thing was that after the panel finished, the moderator made a comment being happy that not as many people wanted to still experimet with Elixir as at the beginning of the panel.

If I were to sum the panel up it would boil down to: dissappointment. I expected interesting, open discussion on possibilities. What I got was quite a boring, cliche driven panel. A panel that (I belive) aimed to assure Ruby developers that Ruby still is THE LANGUAGE and that Rails is still THE FRAMEWORK. I am afraid that's not really true. I don't expect Ruby/Rails to disappear in the nearest future, but I don't think it will stay as popular as it is/was. And this is not only due to emergence of Elixir+Phoenix - Rails today is just one of many web oriented frameworks that it is pleasure to work with. Rails inspired a lot of others, and no longer is the coolest kid on the block.

It is a good summary to point out that at the beginning of the discussion audience was asked if they were willing to try Elixir. At the end the question was asked once again. Not that many hands were floating in the air ;) Was it really 'mission accomplished' as moderator joked? I personally think that this panel discouraged some developers from trying Elixir. Why would you try someting different if your language and framework are... perfect? ;D

It is sad, that so many interesting questions were left unanswered (for example, question about mnesia). This panel could be of much greater benefit to all those who are not (yet) convinced that they should try Elixir, those who would take the extra effort to broaden their horizons.
This post already grew more than I expected, so I will try to answer some of the questions that are interesting, but due to the time constraint didn't have a chance to reach experts.

I think that Wrocloverb 2017 lacked 'an intoduction to Elixir for the masses' type of talk. It could be quite hard for those, not being exposed to what Elixir is, follow the discussion on Elixir and Ruby. I am afraid those Ruby devs, who just hoped to get some key info on Eixir were left dissappointed.

Note: this is all written in a hurry, so I do apologize for all the typos or errors, poorly phrased sentences etc. 

