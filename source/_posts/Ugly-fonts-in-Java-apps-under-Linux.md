title: Ugly fonts in Java apps under Linux
date: 2016-02-05 17:19:55
categories:
- setup
tags:
- configuration
---

What strikes me from time to time is that under Linux all works well... after you spend some time searching for ways to fix things, and make them work *exactly* the way you want them too.

I am really picky when it comes to the UI. I love command line and console, but as I do work a lot with written words... quality of fonts rendering is *extremely* important for myself. 

I am learning RoR at the moment. I've been doing quite some coding recenlty using pure VIM, but decided to give RubyMine a try. RubyMine is very powerful IDE, but under the default JDK/JRE (no difference if this is OpenJDK or Oracle's JDK/JRE) the way it renders fonts is just pain to the eyes. Eclipse renders fonts much better (by default) than RubyMine, and NetBeans is as bad as RubyMine is.

I've spent a bit of a time trying to configure RubyMine so that it renders fonts as nicely as VIM :) but with no success. I was so desperate on this, that I was planning to either switch to another IDE (but Aptana is no go for me) or to go back to pure VIM again.
Fortunately I have found a solution for Debian/Ubuntu:

1) Do not use Oracle's Java
2) Do not use the OpenJDK default repository
3) Add the ```https://launchpad.net/~no1wantdthisname/+archive/ubuntu/openjdk-fontfix``` as a ppa

Install OpenJDK 7/8 from the repo mentioned in point 3.

If you have other flavors of Java installed, use ```sudo update-alternative --config java``` to pick the OpenJDK installed from ```no1wantdthisname``` ppa.

That's it.

And the results? Huge, huge differnce:

Before:

{% asset_img rubymine-ugly-fonts.jpg "Ugly fonts in RubyMine" %}

After:

{% asset_img rubymine-nice-fonts.jpg "nicely looking fonts in RubyMine!" %}

