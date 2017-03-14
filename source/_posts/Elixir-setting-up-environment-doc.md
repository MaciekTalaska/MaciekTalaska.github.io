title: Elixir-setting-up-environment-doc
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

In my last (which was prepared some time ago) I have described how to use asdf for Erlang and Elixir version management.

There is one important thing that was not covered in that post: documentation. Erlang and Elixr they both come with documentation included. For Elixir it is all about using `iex`. For Erlang - there are manpages available. As always - things a bit more complicated when someone uses versions managers (such as asdf/kerl etc). It seems that documentation for Erlang is not properly installed when using asdf-erlang. Issuing `erl -man mnesia` results in 'No manual entry for mnesia' instead of proer manual page being displayed.

I have found a temporary solution for that though: http://stackoverflow.com/a/42053208

The proper solution would be to have documentation files downloaded, extracted and copied as part of the installation process. The manual workaound works for me at the moment, and I haven't found enough time to try to enhance asdf-erlang to be capable of taking care of installing proper version of Erlang documentation.
