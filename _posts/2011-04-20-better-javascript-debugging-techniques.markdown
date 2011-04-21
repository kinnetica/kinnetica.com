---
layout: post
title: Better JavaScript Debugging Techniques
description: JavaScript debugging is notoriously hard, but new tools in Chrome Developer Tools, testing frameworks, and code quality tools make it much easier.
keywords: javascript,debugging,trace,stacktrace,chrome,developer tools,jasmine,javascript testing,testing,tdd,jslint
change_frequency: monthly
---

JavaScript code is notoriously difficult to debug. It tends to fail very silently, and even when modern browsers are able to provide errors and line numbers, these sometimes tend to be unhelpful. As web applications are now relying on JavaScript for critical parts of its appearance and functionality, developing a powerful toolkit for debugging and testing JavaScript code is crucial. 

Here are some tools I recommend:

### Chrome Developer Tools

If you're using Chrome, there are many different tools at your disposal for discovering and debugging JavaScript issues. If something seems to be working incorrectly, simply open up the Chrome Developer Tools console (Cmd-Alt-J on a mac or View -> Developer -> JavaScript Console from the menu). You should see any errors, with associated line numbers, for the page you are currently browsing. You can see similar errors in Firefox by using the Firebug extension.

One new feature in Chrome is the ability to see a stack trace for each error. Just click on the arrow to the left of the error to expand it. This feature becomes more and more convenient as the complexity of your JavaScript program increases, and there are many different paths of possible execution.

Chrome Developer Tools also gives you the power to set breakpoints in your code under the Scripts tab. Simply select the JavaScript file you're trying to debug and click on the line number where you want to set the breakpoint. After reloading the page, Chrome will pause the execution of your script, let you step through it, as well as examine the state of your variables and DOM.

If breakpoints are not your debugging tool of choice, both Chrome and Firefox (with Firebug) support adding debugging statements to your code that get output to the console. To do this, simply use `console.debug()` and pass the variable you want to examine as a parameter.

Chrome has gone a step further and provided a few new console methods for you to use. One of these is `console.assert()`. This method is passed some condition as a parameter, which when evaluated to false, will print a complete stack trace. This can be very useful for validating any invariants in your code. Also, if you want to see a stack trace at any point in the program, you can now throw in a call to `console.trace()`. These new additions to Chrome, as well as some others, were explained in greater detail earlier today in a [post on the Chromium blog](http://blog.chromium.org/2011/04/chrome-developer-tools-understanding.html).

The extensive features in Google Chrome's Developer Tools makes Chrome a very compelling choice for assisting in debugging all of your JavaScript code.

### Jasmine

[Jasmine](https://github.com/pivotal/jasmine/wiki) is a testing framework for your JavaScript code. While JavaScript has never been a language that has traditionally received a lot (or any) test coverage from most developers, this is slowly changing. JavaScript is a much more serious language today than it was in the past, with the introduction of powerful frameworks, faster browser support, and AJAX. As the code we write becomes more essential to the application, we have a responsibility to make sure it's working correctly.

If you're a Rails or Ruby developer who has played with RSpec, you will feel right at home with the syntax. The [Testing JavaScript with Jasmine](http://railscasts.com/episodes/261-testing-javascript-with-jasmine) railscast should get you up and running very quickly.

If you just want to try it out on a simple static site, look at the [example](https://github.com/pivotal/jasmine/tree/master/example) provided in the Jasmine GitHub repository. Once you have all the files downloaded, you can just edit the `SpecRunner.html` file. First, include all of your JavaScript source files, followed by your test files. You should be able to see the results of your tests by simply opening `SpecRunner.html` in your browser.

### JSLint

While [JSLint](http://www.jslint.com/) is not necessarily meant for debugging, it is a very useful tool to make sure your code is clean and following best practices. Run your JavaScript through it once you're finished coding to see what it recommends. Certain design choices made in the JavaScript language tend to cause difficult-to-find bugs. JSLint tries to make recommendations that steer you away from making those type of mistakes. If you have trouble understanding any of its recommendations or don't understand the reasoning behind any of them, reading this [page](http://www.jslint.com/lint.html) should help.

I hope these tips are useful to you. Please let me know if you have any JavaScript debugging tips or tricks of your own.