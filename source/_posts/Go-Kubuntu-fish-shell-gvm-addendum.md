title: 'Go, Kubuntu, fish-shell & gvm - addendum'
date: 2016-01-17 21:03:54
tags: 
- Go
- fish shell
- configuration 
category: programming
---

There is just one important thing that I have missed in my previous post. It all seems to work ok, but if you restart your machine you quickly realize that the ```gvm``` is not available to you anymore. What is the point?
Well... this is due to the fact that after a function is created for fish-shell (as in step 2 in previous blog post) it works... but it is not stored for future use. To do that - there is one single thing required - function has to be saved. This will make it persisted, and such a function will be available to you after your machine is restarted. 

How to save a function? This is extreemely easy, you just type ```funcsave <function_name>``` - in our case (in case of saving `gvm`) it will be: ```funcsave gvm```. That's it. 

Now if you cd to your ```~/config/fish/function``` folder, you will spot the file named ```gvm.fish```. The content of the file is (surprise?) the definition of the ```gvm``` function used by fish-shell (step 2 of the previous blog note). 

I hope it is now clear 
