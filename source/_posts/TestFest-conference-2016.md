title: TestFest conference 2016
date: 2016-02-25 21:22:07
tags:
- software quality
- testing
categories:
- conference
---

On the 20th of February 2016 I have attended a TestFest conference ([PL] http://www.testfest.pl). It was targeted at testers/QAs working in IT industry. I am not one of them ;) but as my friends were organizing the whole event, and they let me know about it - I decided to take part in it.

### Epic Battle: Zombies vs Mutants (Mutation testing) by Tomasz Dubikowski
It was the best talk of the whole conference from my perspective. It was not only a great introduction into mutation testing, but also very funny talk. Tomasz is great at presenting concepts. If you ever wandered what mutation testing was - you should definitely watch Tomasz's talk (it is not available to watch yet). In my opinion the biggest gain there was that Tomasz made sure to present the whole concept on the very well though of example(s). In my opinion it was huge part of the success of this talk. I have watched several talks about mutation testing so far, but not many were close to the quality of the talk given by Tomasz. If you seem to struggle to understand the whole concept of mutation testing - I would strongly advise you to spend ~hour of your life watching Tomasz Dubikowski's talk. Trust me - it will be time well spent.

### Other Talks
Some other talks were mainly adressed to testers (or as Tomasz put that - QA Evangelists :) There were interesting talks on how to test the hardware to be sent into space (small satellites), how big companies from the telco industry make sure that what they develop could cope with high traffic. 

Some other talks were not that interesting for myself (please mind: I am a developer) - for example I haven't gained much from the talk that focused on the need of understanding of RDBMSs for QA person. Everything was already known to me. What stroke me though, was that it seems the "marriage" between QAs and Devs are still... challenging relationships :) I think most of the problems (technical ones) QAs have when aiming at testing particular application are due to the fact that they get very little (if any) help from developers. Yes - we, developers - are to be blamed here.
That is pretty much surprising, as we all should have a feeling that the success is only possible if we all make an effort to build the product of the best quality possible. So - lesson for us - developers - we should be more open, and more willing to share our knowledge with QAs.

I have missed two last talks: 
- "Wyzwania w automatyzacji WebDriver" (Challenges in WebDriver automation) by Tomasz Fajks, Tomasz Bień
- "Narzędzia do zautomatyzowanego testowania bezpieczeństwa aplikacji WWW" (Tools for automated security testing for web applications) - by Borys Łącki

I hope that videos will be available on the TestFest's youtube channel (https://www.youtube.com/channel/UCsDeChNGyDDHTevmoC3DrEQ) soon.

### Workshop (errors prediction)
I have missed the 2 talks mentioned above only because I have decided to join one of the workshops, namely the one entitled: "Predykcja elementów błędogennych w kodzie w praktyce" (Prediction of error causes in practice) - by Jarosław Hryszko. I had no expectations for this workshop whatsoever, but I thought that I know nearly nothing about the subject, so there was a high chance for myself to learn something. And I must say I wasn't wrong with my reasoning ;)

Have you ever heard of KNIME (http://knime.org) ? I have not heard about it as well :) So this is Eclipse based tool that allows you to create workflows for data analysis (as I understand). The great power of this solution comes from available "boxes" (components) that are ready to use. These are of different kinds:
- data input (reading from various files)
- data transformation (different techniques/algorithms are available)
The outcome of the whole workflow is mathematical model, that could be later on used to process another set of data. 

At the beginning we were all given a very short introduction to the KNIME platform. Jarosław explained how to create workflows, how to connect elements (boxes/components) together, how do we make sure there are no errors etc. Jarosław mentioned that the tool is so easy, that everyone who is capable of using a mouse should be able to use. 
The last part of the workshop was the most challenging one. Jarosław explained us the real power behind KNIME - ability to create models based on the data provided, and analyzing data with the help of the models.

So... is there any possibility to predict where errors in code could/would occur? The only technique I knew so far was as follows:
- gather system statistics (especially focus on measure cyclomatic complexity and similar code metrics)
- gather data on which particular files in the repo are the ones that are being changed most often

Create a 4 section box, having following groups:
a) complicated, frequently changed
b) complicated, infrequently changed
c) non-complicated, frequently changed
d) non-complicated, infrequently changed

Those components/source files that belong to the 'A' group are those who are most likely to have new bugs introduced in. Those in the 'B' group, probably are buggy (or were buggy) and we should make sure that we test them properly. 'C' group contains code which is usually frequently changed due to changing requirements, but if not many errors were introduced so far - we should not worry about this group as much as of 'A' & 'B'. The last area is the one that is of the least importance (from the perspective of possibility of new bugs being introduced).
That approach should not be anything new for anyone who spotted the correlation between frequent changes & code complexity and number of bugs found in particular source files.

What Jarosław demonstrated was much more sophisticated. There were 3 requirements:
a) code metrics
b) history of bug fixes (based in Jira, if I remember correctly)
c) data from repository (frequency of changes - if I recall)

After the model was created it would be possible to have another code metrics applied as input for the workflow, and get prediction on which parts of the application code are very vulnerable to bug introduction. That approach literaly blew my mind out.

Of course, this requires a lot of discipline (input data - this is not something you can 'borrow' from someone else - another team/company). The other thing that could be a bit of a problem is: what happens if team gets changed: new people join and some other leave the team? The overall experience of the team changes. That could definitely impact the structure of the code, and its quality.

Anyway, I think it was very well spent ~2 hours. I may not use this technique, but being aware of such an approach is (in my perspective) a real eye-opener.

Jarosław's bio [PL]: http://www.testfest.pl/wordpress/?page_id=973
Jarosław's home page (including some materials we have used during the workshop): http://hryszko.net/
KNIME tool: http://knime.org

### Summary
So even though TestFest was not target at developers, I definitely think it was worth to spend whole Saturday in the building of the local Technical University. I have had a chance not only to get to know some interesting personas, but also learned couple of things.
I have meet with my colleagues (organizing the event) later in the evening at the after party, and we have spent good couple of hours discussing different topics (not all related to IT at all), enjoying good food and beverages.

Do I plan to show up on TestFest next year? Definitely. I hope I will meet some of the people I meet the next year as well!

Please note, that talks, conference site etc. are in Polih only.
TestFest conference site [PL]: http://www.testfest.pl
TestFest conference YouTube channel [PL]: https://www.youtube.com/channel/UCsDeChNGyDDHTevmoC3DrEQ
