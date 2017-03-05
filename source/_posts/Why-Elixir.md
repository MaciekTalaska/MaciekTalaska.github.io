title: Why Elixir? 
date: 2017-03-04 22:32:23
tags: 
- programming
- my opensource projects
- Elixir
category: 
- get-noticed-2017
---

In my first blognote related to this years edition of "Get Noticed" I have mentioned that I am planning to develop web application using Elixir & Phoenix. Why Elixr? 

I have a chance to develop web applications using variety of technologies: C# + ASP.NET & ASP.NET MVC, Python + Tornado, Ruby on Rails, JavaScript + NodeJS + Angular, Meteor (using Blaze as the frontend technolgy). Some technologies were more and some were less "developer friendly". If I were to sum up what technolgies were the most fun to use I would say: RoR and JavaScript frameworks. MetorJS was a bit more fun, but NodeJS + Angular + MongoDB is something more solid, and still used even today (apart from the fact that teams are migrating from Angular 1.x). C# + ASP.NET/ASP.NET MVC were a bit less fun, altghough ASP.NET MVC was much better and I liked it a lot more than classic ASP.NET. What I didn't particularly like about MS tech stack was that it was more of a blob than just language + technology stack. What I mean is that it is rather impossible to create something more complicated NOT using Visual Studio. Generators (as yeaoman, rake etc.) were not available at that time, so there was not a chance to use something else for working with code than Visual Studio. Everything was IDE driven. If there was a need to add additional fields to a database, or create new tables - all these actions were invoked from withing the IDE. It was so much different to the approach I could take develiping applications with pure JavaScript or Ruby. Having powerfull command line tools I felt I had more control over the process of application development. And I also had the feeling that I understood better what is happening and why.
So - the first thing would be "openess" or simply - technology being open source. Or even free - in terms of leaving all the decisions to the user.

## Scalability
My personal opinion is that web applications are facing different problems that 10 years ago. Succesful applications right now often get extremely popular in a very short time. This means that it is important to design application with scalability in mind. And that is not so easy. The number of problems one has to face when it comes to designing scalable app is huge: beginning with responsiveness of the frontend itself, scalability of the workers, session management, and (probably the most complicated) picking up proper approach related to data storage. These are all non trivial problems. 

Elixir is based on Erlang virtual machine. Erlang on the other hand is a language developed in 1986 by Swedish company Ericsson. Erlang was born alltogher with OTP - Open Telecom Platform - which was used to to control switches (as far as I understand at the beginning the aim was to control and connect phone calls). Erlang is being described as general purpose, concurrent, fault-tolerant & functional programming language. The concurrency in Erlang is achieved by using actor model, which is extremely interesting concept. In short - Erlang is capable of spawning hundreds or even mant thousands of processes in a very short time. These processes are much lighter than OS processes, and are controlle by Erlang VM. Important thing is that Erlang comes with a lot of tooling for controlling processes. Elixir as a language based on Erlang benefits from all that.

As I see it nowadays - scalability becomes more and more important in the are of web applications development. Elixir seems like a perfect fit here. Why not Erlang itself? Well - partially because Elixir syntax seems more appealing to me.  

## Functional Programming
I have a strong feeling that functional programming is one of the most important concepts that each and every developer should deeply grasp. I was taking some Scala and Haskell courses back in the past, but I lacked a proper "battlefield" to test my knowledge. I want to make an effort this year and develop my skills in the area of functional programming. What better opportunity than creating an application using functional programming language?

## Mature technology
I have already mentioned that the technology Elixir is based was created back in the 1986. It means that it is more than 30 years old. Quite a lot of time to prove its maturity.


## Friendly community
What is unique in Ruby community is its openness and friendliness. I had zero problems solving problems I bumped on, when developing my RoR applications. A lot of resources are available, and people in general are very happy to help someone who is not familiar with the technology.
I have the feeling that the same is true about Elixir community. Maybe it is due to the fact that a lot of people who are interested in Elixir have Ruby background, but I am not sure if this is the (only) case. 

## Hype
Hype may not be the best word... I have a strong feeling that there is a lot of interest in Elixir. Not only from the developers but also from companies. More and more companies are evaluating Elixir and check if it is a good fit for their needs. I see a constant rise in interest of hiring people who are familiar with Elixir. And this interest is no longer only from the companies located on the West Coast of US - there are more and more companies using Elixir located in Europe. I treat the whole adventure as an investment for the future.
