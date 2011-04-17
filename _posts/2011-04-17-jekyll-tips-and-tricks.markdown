---
layout: post
title: Jekyll - 7 Tips &amp; Tricks
description: Useful tips and tricks for setting up your personal blog using Jekyll.
keywords: jekyll,tips,tricks,documentation,samples,automatic refresh,drafts,metadata
change_frequency: monthly
---

Instead of going with Wordpress or Tumblr for this blog, I decided to try out [Jekyll](https://github.com/mojombo/jekyll). I was very happy with the experience, and thought I would share some of the lessons I learned to hopefully make the process easier for others.

1. Jekyll has very helpful documentation available on their GitHub [wiki](https://github.com/mojombo/jekyll/wiki). However, I found it hard to find all the available content simply by browsing the links on the wiki Home page. Once you have the basics up and running, I suggest clicking on [Pages](https://github.com/mojombo/jekyll/wiki/_pages) to see all of the available material. The [mailing list](http://groups.google.com/group/jekyll-rb) is also a good place to go for help.

2. The documentation also has a [listing of sites](https://github.com/mojombo/jekyll/wiki/Sites) that were created using Jekyll. Almost all of them have code posted on GitHub. This is definitely worth sifting through to get a better idea of how Jekyll works and how it can be used to accomplish your vision.

3. While you're initially developing your site, it's very convenient to be able to see changes automatically as you make them without having to constantly restart the Jekyll WEBrick server. Make sure to either put `auto: true` in your `_config.yml` or start the server using the `--auto` flag to see your changes in real time. This is not the default behavior. Other customizations to your `_config.yml` can be found [here](https://github.com/mojombo/jekyll/wiki/Configuration).

4. While working on writing posts, there are two different methods for keeping 
   posts from appearing when your site is generated. The easiest way is 
   including `published: false` in the [YAML front 
   matter](https://github.com/mojombo/jekyll/wiki/YAML-Front-Matter) of that 
   post. 

   Personally, I found it helpful to create a separate `_drafts` directory. This 
   directory holds all of my unfinished posts. When the post is ready, I simply 
   rename the file to reflect the correct date and copy it over to the `_posts` 
   directory.

5. If you're going to install and enable pygments, make sure you remember that 
   you will need to provide styles for syntax coloring. For my site, I 
   experimented with some of the stylesheets found 
   [here](https://github.com/richleland/pygments-css). You will need to change 
   the default class in the styles from `.codehilite` to `.highlight`.

   One other cool feature with using pygments is the ability to add line 
   numbers to your code. For instance, if you were writing Ruby code and wanted 
   to include line numbers, simply surround the code with `{ % highlight ruby 
   linenos % }` and `{ % endhighlight % }` (omit the spaces between curly brace 
   and percent sign). If you don't want line numbers, simply don't include the 
   `linenos` keyword.

6. If you are not yet familiar with Liquid, it's worth spending a little time getting up to speed. I've found the best resources to be the [Liquid for Designers](https://github.com/tobi/liquid/wiki/liquid-for-designers) guide on GitHub and the [documentation](http://liquid.rubyforge.org/).

7. One of the convenient features of Jekyll is the ability to add metadata to 
   all of your pages in the front matter section. By using the YAML `key: 
   value` syntax, you can define your own custom variables and reference them 
   within your site.
  
   One use for this is being able to change the page title depending on 
   the page being displayed. For instance, if you have `Ham: Is It Superior 
   To Bacon?` as the title in the front matter of a post, having `<title>{ { 
    page.title } }</title>` (omit the spaces between the curly brackets) in your 
   layout file will set the page title to `Ham: Is It Superior To Bacon?` within 
   that post.
  
   Another clever use of this trick is to add a description and keyword custom 
   variable on each post and page. You can then include these custom variables 
   within a description and keywords meta tag in your template. The 
   description will usually get picked up by Google and displayed in its search 
   results. While [Google ignores meta  keywords](http://googlewebmastercentral.blogspot.com/2009/09/google-does-not-use-keywords-meta-tag.html), other search engines might still use them, so it might 
   make sense to include them as well. Doing this will make it easier for search 
   engines to display a relevant description and categorize all of your 
   indexed pages.
   
The source code for my personal site is available on GitHub [here](https://github.com/kinnetica/kinnetica.com). Feel free to use it to learn or as a starting point, but please make sure to remove all site specific code (e.g. Google Analytics snippet).