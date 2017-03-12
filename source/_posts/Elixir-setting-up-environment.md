title: 'Elixir: setting up environment'
date: 2017-03-12 23:31:37
category:
- get-noticed-2017
- programming
- functional programming
tags:
- Elixir
- Erlang
- fish shell
- asdf
- asdf-erlang
- asdf-elixir
---

One of the first things that is required when starting with new (programming) language is... to have compiler/interpreter installed and prepare the environment. Cliche...

I am happily using nvm (for NodeJS) gvm (for Go) and rvm (Ruby) for quite a long time, and I started looking for something similar for Elixir and Erlang.
I wasn't very lucky at first, as my first approaches were not really successful. It was mainly due to the fact that I am happy user of fish shell, and I don't want to give up using it (even in favor for zsh).

I think I am this kind of a person who really tries to makes everything complicated ;) Even though I could have Elixir and Erlang easily installed issuing something as simple as "sudo apt install erlang elixir" I am not really keen on doing that. Two reasons:
- in most cases versions of the compilers/interpreters in system repository are really far from the latest (and that gets worse and worst as time passes by)
- in such a scenario it is not possible to have many versions of a specified compiler / interpreter installed. And sometimes it is a must (maintenance of some old application etc.)

## asdf to the rescue! 

Back in summer 2016 I was quite successful using hybrid approach. I have used asdf () for Erlang and kiex for Elixir. Asdf was required only to get specified version of Erlang. Asdf was not accessible for me via fish (so I had to use bash for asdf) but luckily kiex was running all fine under fish. The whole thing didn't bother me that much, and I have been using such approach for quite a while. Today - as I was trying to set up environment on another machine - I have realized that asdf does support fish shell right now :) What a nice surprise. It all became so easy right now.

Asdf seems to be much more flexible than the other version managers that I am using. Asdf does not focus on one particular language. There is a concept of plugins for asdf which allow it use asdf for managing versions for many different languages. Installing plugin(s) is the second thing you will have to do right after you have asdf installed. But if you get to that point, installing new version of Erlang becomes as easy as:

`asdf install erlang 19.2`

which (to me) is as simple as `sudo apt install erlang` but, of course, using asdf has advantage of installing specific version(s)!

Asdf is very simple but powerful. All your version management is literally under your fingertips.

So, if you're like me, and you like to have 100% control of the versions of compilers installed - please try asdf. This is a great tool!

I am actually thinking if it would be a good idea to try asdf for managing NodeJS, Go and Ruby versions (oh, and I am planning to get my hands dirty a bit with Clojure and Rust in the nearest future, and asdf supports these as well...) 

## Caution: dependencies

It is essential to study erlang plugin home page. It brings a lot of info on dependencies that are required to have Erlang offer everything. I haven't paid enough attention first, and ended up with environment I wasnt able to run obser (or debugger). This particular issue is easily fixed by installing dev version of wxwidgets library (and rebuilding Erlang, unfortunately...). 

So if you encounter "wxe_driver.so" related error whenever you try to launch observer/debugger - you know what to do :)

Another thing worth mentioning is having xsltproc installed, so that documentation could be properly created during the process of installing Erlang.

## Elixir

Having Erlang installed, and being familiar with asdf, bringing Elixir on board is piece of cake (assuming you have elixir plugin for asdf installed first):

`asdf install elixir 1.3.4`

Elixir installation is much, much faster than Erlang. 

## Disadvantages of asdf

The only disdvantage of asdf I can think of right now is that installing new version of Erlang does take time. Why? It is not as simple as just retrieving binary from some repository. Source code for specific version is being downloaded and then built. It all take several minutes on my machine - but hey, how often do you install new version of your favorite compiler? Personally I think that flexibility described is worth waiting from time to time to have a specific version of the language installed. It is important to note that removing version previously installed is almost instant. 
Note: after adding additional libraries (wxgtk-dev among others, so that I can start observer and debugger) compilation time now takes significantly longer. It is althought the price I am still willing to pay for the flexibility that asdf brings.

After a quick break from writing this blog post, I realized that there is one more thing which I don't particularly like about asdf. Installing a new plugin requires one to go to asdf project site on github and check what is the plugin repo url - when you have it, a simple `asdf plugin-add elixir https://github.com/asdf-vm/asdf-elixir.git` (for Elixir) will do. I'd rather have possibility of doing all that via command line. But that a really minor thing.
