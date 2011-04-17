---
layout: post
title: CSS Selection Attribute
category: css
description: Details about how the CSS selection element works.
keywords: css,css3,selection,highlight,element
change_frequency: monthly
---

One of the lesser-known features of CSS is the option to style text selected by the user. This is achieved using the `::selection` pseudo-element. Here is an example:

{% highlight css %}
::selection {
  color: #000;
  background: #fff;
}

::-moz-selection {
  color: #000;
  background: #fff;
}
{% endhighlight %}

Firefox currently requires the `-moz` preface when using the element. This element will work on all modern browsers (Chrome, Firefox, Safari, Opera, IE9). There is no support for earlier versions of Internet Explorer.

Although a feature like this should be used sparingly, sometimes it can be used to produce good-looking results. An example of where this feature is used well is Paul Irish's [CSS3 Please](http://css3please.com "CSS3 Please") site.

The `::selection` pseudo-element was originally written in the CSS3 draft spec, but was later removed. However, it has already been implemented in all major browsers and should continue to be supported in the future.

Note: Only the `color`, `background`, and `background-color` CSS properties will work with `::selection`.

More Resources:

1. [MDN Documentation About ::selection](https://developer.mozilla.org/En/CSS/%3A%3Aselection)