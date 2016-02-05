title: Go 1.5.x on Kubuntu using fish shell and gvm 
date: 2015-11-07 23:16:08
tags: 
- Go
- fish shell
- configuration
category: programming
---

I got really interested in Go and I am learning it in my spare time. Unfortunately the verion of Go that is available via Ubuntu repository is very old (at the moment of writing this it was 1.2.x). It was not good enough even for learning purposes.

I wanted to use the very latest version of Go (1.5.x) and started looking for an PPA that would allow me to install the newest version. I quickly found one: https://launchpad.net/~evarlast/+archive/ubuntu/golang1.5 Unfortunately I quickly realized that it may not be the best idea. 

What if need to use two different versions of Go? How do I manage them?

The best thing is to use something similar to nvm (NodeJS Version Manager) or RVM (Ruby Version Manager). As I am using fish shell instead of bash, things are a bit more complicated. There are couple of steps required to have Go 1.5.x installed on Linux, and make the whole thing work with fish shell.

1. Install gvm (https://github.com/moovweb/gvm)
2. Make gvm work with fish shell (https://github.com/moovweb/gvm/issues/137#issuecomment-131400212). You may need to install bass first (https://github.com/edc/bass)
3. ```gvm install go1.5.x``` will not work, as Go 1.5.x requires Go 1.4.x for compilation. Install Go 1.4.x first (```gvm install go1.4.3```)
4. ```gvm install go1.5.x``` will fail again, due to the fact that it will be unable to find Go 1.4.x. You will probably see similar error message
{% codeblock %}
ERROR: Failed to compile. Check the logs at /home/<username>/.gvm/logs/go-go1.5.1-compile.log
ERROR: Failed to use installed version
Installing go1.5.1...
 * Compiling...
{% endcodeblock %}
In my case the log content was: 
{% codeblock %}
 ##### Building Go bootstrap tool.                                             
 cmd/dist
 ERROR: Cannot find /home/<username>/go1.4/bin/go.
 Set $GOROOT_BOOTSTRAP to a working Go tree >= Go 1.4.
 ./make.bash: line 121: /home/<username>/go1.4/bin/go: No such file or directory
{% endcodeblock %}
5. Execute the folling commands to help gvm to succesfully compile Go 1.5.x (this is based on the discussion: https://github.com/moovweb/gvm/issues/155#issuecomment-135855340):
  a) ```gvm use go1.4.3``` 
  b) ```set -x GOROOT_BOOTSTRAP $GOROOT``` 
  c) ```gvm install go1.5.1``` 

That should be all fine right now. Go 1.5.x should be installed on your machine (side by side with the Go 1.4.x that was used required to compile the newest version of Go).

Happy coding (in Go!)
