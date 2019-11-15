title: In the search for the perfect NodeJS version manager (again?)
date: 2019-11-11 19:13:18
category:
- setup
tags:
- asdf
- nvm
- NodeJS
- fnm
---

Some time ago I shared how much I liked the way `asdf` simplified version management of some of the developer tools (mostly: programming languages) for me. 

`asdf` is mature and offers a lot of ready to use plugins. It syntax is easy to remember and concise. But I newer actually used it for NodeJS version management. Why? Mainly it was due to the fact that I was pretty happy with `nvm` that I started using couple of years ago. `nvm` has unique ability to install new version of NodeJS reinstalling all packages (global ones) that are installed for the currently used version, the syntax is as follows:

`nvm install <new_version> --reinstall-packages-from=<old_version>`

That is super convenient, as it happens automatically, so after installing new version you end up with all the packages you need. Awesome. 

`nvm` just doesn't seem to work well under `fish`. For some strange reason I had to remember every time on setting default version, otherwise `npm` and all the globally installed packages were not seen as available. This was a bit of pain.
I have spent some time trying to find some solution for this issue, but nothing worked as I wanted. I tried some additional wrappers - but these affected either `fish` start performance or were not convenient for me to use.

My friend suggested me to try `asdf` for NodeJS - and I was all like 'why haven't I thought of it before'?

## ASDF

Installing a new plugin for `asdf` is super simple:

`asdf plugin-add nodejs` 

That's it!

Installing a new version of NodeJS is not harder either:

`asdf install nodejs <version>`

So right after roughly a minute I had `asdf` supporting NodeJS versioning. The very last thing that I had to do was installing packages I usually need. I did that manually by creating a list of packages installed (using `npm list -g --depth=0`) and then passing package names to the `npm i -g`. And it was this moment that I realized some strange. It seem that installing packages took ages in comparison with `nvm`! 

At first I thought this was just my impression, there were dozens of packages to install, each having some dependencies... I must have been wrong.
Just for the future convenience I have spent some time in the evening developing small script that would automate installing new version of `NodeJS` and installing global packages. It took me some time (as I wanted to have it polished). If you're curious - you may find it in my `dotfiles` repository on my github (direct link: https://github.com/MaciekTalaska/dotfiles/blob/master/asdf_reinstall.sh).

I have installed another `NodeJS` version and run the script to test it (using `time`). The times I got were pretty horrible:

| name | time |
| --- | --- |
| nvm | 2:41.76 |
| asdf | 26:23.49 |

So I started reading about the issue, and it seems this is something that community behind `asdf` (or `asdf-nodejs` specifically) is very well aware of:

* https://github.com/asdf-vm/asdf-nodejs/issues/104
* https://github.com/asdf-vm/asdf-nodejs/issues/46


I have experimented with the `SKIP_RESHIM=1` flag, that help a lot, but not as much as I hoped for, and the times were not even close to those I have experienced when using `nvm`.

| name | time |
| --- | --- |
| nvm | 2:41.76 |
| asdf | 26:23.49 |
| asdf (SKIP_RESHIM=1) | 8:33.94 |


I knew, I felt there just "has to be a better way"...

I have tried some other version managers for NodeJS. I have re-evaluated `nvm` but experiencing the pain of setting default `NodeJS` version each time... no, it was not something I wanted to get back into.

And then at some point I have found... `fnm`!

## FNM to the rescue!

So `fnm` stands for `Fast Version Manager` and it does what it says. It is fast. It is as fast as `nvm`. Its syntax is quite easy to get used to, but more importantly it works perfectly well under `fish`. The only problem I have encountered was that at first it didn't seem to detect being run in `fish` environment. After looking at the code I have realized that it (`fnm`) relies on `$SHELL` variable to be set properly. For some reason I have had it set to the path to the shell I was using... after fixing that (just adding `set -xg SHELL /usr/bin/fish` to my `config.fish`) and reinstalling all went well.

The times using `fnm` are as follows:

| name | time |
| --- | --- |
| nvm | 2:41.76 |
| asdf | 26:23.49 |
| asdf (SKIP_RESHIM=1) | 8:33.94 |
| fnm | 2:44.22 |

So I was quite impressed with the performance. I was happy `fnm` works well under `fish`. Using it was not a hard task either. Interacting with `fnm` is pretty similar to `nvm`:

* listing installed versions:

`fnm ls`

* listing available versions:

`fnm ls-remote`

* installing new version:

`fnm install <version>`

* making installed version default version:

`fnm default <version>`

So the very last thing I needed was to change the script I have originally developed for `asdf-nodejs` so that it supports `fnm`. If you would like to have a look/use it, you could find it in the same repo: https://github.com/MaciekTalaska/dotfiles/blob/master/fnm_reinstall.sh

## Conclusion

I am happy that I have found a perfect solution for myself. It did take me some time, but now this is a pure joy working again. 

Go and check `fnm` there is a high change you may want to switch as well (especially if you're `fish` user, or if you are using `asdf` currently and are not happy with how it performs).
