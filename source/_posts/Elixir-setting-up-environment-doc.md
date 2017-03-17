title: Elixir setting up environment part 2: documentation
date: 2017-03-14 20:11:53
category:
- get-noticed-2017
tags:
- programming
- Elixir
- Erlang
- functional programming
- my open source projects
---

In my last post (which was prepared some time ago) I have described how to use asdf for Erlang and Elixir version management.

There is one important thing that I have not covered: documentation. Erlang and Elixr both come with documentation included. For Elixir it is all simple as using `iex` and its `h` helper (read more about it: https://hexdocs.pm/iex/IEx.Helpers.html). 

For Erlang - there are manpages available. As always - things a bit more complicated when someone uses versions managers (such as asdf/kerl etc). First of all, you can't expect that it would be possible to access Erlang's manpages usin system 'man' - unfortunately this is not how things work (maybe if you install Erlang using repository instead of version manager such as asdf...). The other important thing is that documentation for Erlang is not properly installed when using asdf-erlang. Issuing `erl -man mnesia` (mnesia being name of the module) results in 'No manual entry for mnesia' instead of proer manual page being displayed.
I have found a temporary solution for that: http://stackoverflow.com/a/42053208

The proper solution would be to have documentation files downloaded, extracted and copied as part of the installation process. The manual workaround works for me at the moment, and I haven't found enough time to try and enhance asdf-erlang to be capable of taking care of installing proper version of Erlang documentation.

It has been discussed that Elixir's iex helper should be able to display documentation for Erlang modules (https://github.com/elixir-lang/elixir/issues/3589). Unfortunately it seems that at the moment there is no working solution for such a behavior. There are some alternate solutions, but I haven't tried any yet.

Interesting solution for viewing Erlag/Elixir documentation is Zeal (http://zealdocs.org). It is available for Linux, MacOS and Windows, and allows easy browser Erlang and Elixir modules. For some it may be much more convenient to use Zeal instead of using erl or iex depending if module is part of Elixir or Erlang.
