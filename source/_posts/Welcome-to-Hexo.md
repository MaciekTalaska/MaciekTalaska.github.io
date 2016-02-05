title: Checking out hexo! 
date: 2015-08-16 12:30:08
tags: 
  - hexo
  - Nikola
  - Jekyll
  - static site generators 
category: blogging
---

I was thinkig for quite some time how to migrate my old blog from Wordpress to some other blogging platform. Couple of reasons why I started thinking of giving up Wordpress:
* Wordpress is complicated, offers a lot of plugins, and this makes it vulnerable to 'hacking' 
* I don't think I really need the flexibility that Wordpress offers. I think for me it is just too much. I am not planning to write blog with someone else (so I don't need platform which supports many authors)
* Wordpress requires hosting. And that costs.

Some time ago I've bumped on couple of people saying that static sites generators are great for blogging purposes. It seemed to me a good idea having my blog hosted on github, so that I can have all the things in one place. 

I've heard about Jekyll, Nikola, Pelican but I knew there were many more. I had to figure out what my needs are, and after a short while, I came up with the most important features my preferred blogging platform should offer:
- good support for code snippets (as I will be using this mainly for my programming related blogging)
- support for plugins (for example: I want to be able to use disqus for comments)
- offering some nice themes, so that I can pick something for the very beginning

My workmate suggested me to have a look at Nikola. The installation was easy (I've used virtualenv so not to spoil my environment). It took me a bit to have a first blog post in the shape of my desire. In a short time I've learned how to work with Nikola. I think Nikola is a great piece of software. I was quite amazed when I discovered how easy it was to install additional theme. It wasn't much harder to change bootstrap's based theme (for the bootstrap based themes). All with just providing couple of arguments to Nikola. Although... I wasn't very happy with Nikola. Mainly because:
- Nikola is quite slow, re-generating your site takes quite some time. As I was playing with quite many themes, and was doing a lot of tweaking - that was something hard not to notice
- I've spent some time searching for nice themes, and... I was quite dissappointed. I couldn't find a nice, easthetic theme, that would render code snippets in a fancy way. Some themes looked better in general, some were not that nice, but rendered code snippets better. All in all I haven't found one theme I could be happy with. I had a quick look at Pelican (http://blog.getpelican.com/) (which is another static site generator written in Python) and it seemed to me that Pelican offers nicer themes.
- my feeling is that there are not many plugins, and that the community behind Nikola is not very big

After my experience with Nikola, I decided to give some others platforms a chance. I've made some research, and found a site that lists many static sites generators: https://www.staticgen.com/ It is definitelly more than enough. I was amazed how many generators are there. Not only for Python and Ruby, but also for functional languages (Haskell, Scala) and some really exotic languages such as Racket (https://www.staticgen.com/frog).
One of my thoughts was that I should probably go with Jekyll as it has the biggest community, dozens of themes and plugins. What's more, I think that in comparison to Nikola, it may be easier to find some articles on how to change things in Jekyll. I was pretty much set for trying Jekyll, when I spotted Hexo (https://www.staticgen.com/hexo).

Hexo is written in JavaScript and uses NodeJS. One of the biggest advantages is Hexo's popularity: it is ranked 4th when taking github stars. Developers working on Hexo claim it is very fast. And comparing to Nikola... I must say that this is true. Hexo is even easier to set up than Nikola (or maybe it is just me being more fluent with JS stack than Python). If you already have NodeJS on your machine, there is just one package to install. After about a minute I had my "blog" created. Within next couple of minutes I had couple of sample notes, with codeblocks and gists - I decided it looked better than what I was able to create using Nikola. I've spent next hour (or two) playing with themes, and making my own modifications of themes. I am pretty happy with what I have achieved so far. There are couple of things I will need to change, but I guess I am good to go with what I have.

Hexo supports codeblocks...

this is how it highlights Python...

{% codeblock somepy lang:python %}

import sys 

def my_func():
  print(sys.info)

if __name__=="__main__":
  my_func()

{% endcodeblock %}          
        
<br/>

JavaScript: 
{% codeblock some simple AngularJS controller lang:javascript %}
angular.module('angularFullstackApp')
  .controller('CategoryCtrl', function ($scope, hierarchy, $location) {
    $scope.message = 'Hello';

    $scope.categories = [];

    $scope.populateCategories = function(allCategories) {
      $scope.categories = allCategories;
    };

    $scope.categoryClicked = function(categoryId) {
      console.log('category clicked: ', categoryId);
      $location.url('/topics').search('category',categoryId);
    };

    hierarchy.getAllCategories().then($scope.populateCategories);
  });

{% endcodeblock %}

<br/>

...and Go:
{% codeblock lang:go %}

package main

import "fmt"

func main() {
  fmt.Println("Hello World from Go!")
  for i := 1; i < 20; i++ {
    var t = ""
    if i%2 == 0 {
      t = "even"
    } else {
      t = "odd"
    }
    fmt.Printf("Number: %02d binary: %05b octal: %02o %#x\t is %v\n", i, i, i, i, t)
  }
}

{% endcodeblock %}


and this... is how Hexo displays gists:

{% gist 38c4ca8e73d9792f8eae %}


To sum up: I have created my main github page and within minutes I had it published.

I haven't thought that setting up new blog using static site generator will be so much fun. I regret I haven't devoted some time to do it much earlier this year... anyway, I hope that this blog is going to be an opportunity to share what I learn.

As for the moment, the only thing that bothers me is: how do I write blog notes using differnt machine than the one I have everything set up? With Wordpress and other dynamic bloggin platforms it was easy - most of them offered some kind of web interface (administration panel) one may use to write a blog note. With Hexo this is not the way. I will need to think of some way to make it possible. I will post if I have something to share on this topic. 
