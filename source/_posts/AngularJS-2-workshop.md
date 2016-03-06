title: AngularJS 2 workshop
date: 2016-03-06 18:08:41
categories:
- workshop
tags:
- programming
- AngularJS
- AngularJS2
- TypeScript
---

Last Saturday I have attended AngularJS 2.0 workshop organized in Wrocław. The event has been organized by DevMeetings (http://devmeetings.pl), started ~9 am and finished rougly 6 hours later.

Hosts were employees of LiveChat (https://www.livechatinc.com/). One of them - Wojciech Kwiatek - gave a talk on AngularJS2 based on their experience at one of the local tech groups. LiveChat decided to switch to AngularJS2 couple of months ago - even though AngularJS2 was not stable at all at that time (they have jumped on the AngularJS2 bandwagon when the whole thing was still in alpha!). It seems they are still pretty happy with the decision. I know that they have been looking at ReactJS as well, but decided that ReactJS may not fit that well into their usecase, and they would need to create a framework from many libraries on their own - so the 'completeness' of AngularJS2 was also important. 
It was great that hosts had real experience with AngularJS2, and not only "played with it" at home :)

Two skeletons of the apps were prepared - one using gulp, and the other utilizing webpack. If you would like to have a look, the webpack version is freely available on github: https://github.com/wkwiatek/angular2-webpack2

The whole agenda was as follows:
1. Introduction to AngularJS2
2. Components
3. Events
4. Pipes
5. Services and Dependency Injection
6. Forms
7. Http+Rx.js
8. Routing

It was quite a lot of stuff (mostly brand new to most of the attendees) and I don't think a single person has managed to finish all the tasks. I have personally go through the first 6 of them, but haven't touched Http+Rx.js & routing at all.

I especially liked how forms are implemented in AngularJS2 - that is a common thing for web developers to create, and it is not of minor importance. We had interesting discussion on forms in ReactJS at one of the last local tech group meetings. Yes... forms are things you just can't escape from :)

What I lacked a bit was how to structure the whole application. I have spotted that many attendess just took the "finished? go with the next task" approach, and had most of the code in single .ts file. I just wanted to avoid that, and spend some more time on re-structuring the application, so I had everything (classes, components) in separate files.

Summary:
I am happy I have attended the event. I only read about AngularJS2 before, and apart from tiny snippets, I have not written any AngularJS2 code. This was the best opportunity to get more familiar with the technology, create something bigger, and get the 'feeling' of the new, upcoming and technology.

The event was another opportunity to do some more coding in TypeScript. I am not sure if I like it or not... on one hand it seems to mee just too much of a 'C# for JavaScript developers' type of approach, I realize that there is additional effort required to have type definition for all the libraries you use. But on the other hand - I think that TypeScript may allow for further improvements of JavaScript performance (thanks to type annotations and optimizations that could be possible to achieve thanks to it).

Thanks to Wojciech Kwiatek, his friend from LiveChat (sorry, forget the name) and DevMeetings team for making this event happen!

