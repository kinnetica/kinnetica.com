---
layout: post
title: Pretty Printing Minified JavaScript for Easy Reading and Debugging
description: Minified JavaScript makes examining the code in the browser very difficult. Chrome Developer Tools now lets you pretty-print the output for easy viewing.
keywords: javascript,minified,obfuscated,javascript format
change_frequency: monthly
---

Having trouble trying to read and debug minified JavaScript in the browser? Don't worry. Newly added pretty printing in the Chrome Developer Tools is here to make it much easier.

For instance, here is a minified script being displayed within the Chrome Developer Tools:

![Minified JavaScript in Chrome Developer Tools](/images/minified_script_without_formatting.jpg)

By clicking on the curly brace ("Pretty Print") icon in the bottom left corner, the JavaScript is transformed into something that is both easy for humans to read and easy for setting breakpoints.

![Minified JavaScript in Chrome Developer Tools With Formatting](/images/minified_script_with_formatting.jpg)

This feature is now available in both the Chrome Dev and Canary builds for Mac and Windows.