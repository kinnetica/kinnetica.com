---
layout: post
title: Automatically Generating Sitemap.xml Files For Jekyll
description: A plugin to create sitemap.xml files automatically for Jekyll.
keywords: jekyll,jekyll,plugin,plugin,sitemap.xml,generated,automatically,sitemap,seo,search engines
change_frequency: monthly
---

### Why Provide A Sitemap.xml File

Sometimes, crawlers just need a little help. Who can blame them? With hundreds of millions of websites on the internet for search engines to index, no wonder they might benefit from a boost. One way to help crawlers is by providing a sitemap.xml file. Not only does this file list all of the pages on a site that you want to make sure are indexed, but it can also provide useful metadata about each of these pages such as the last modified date, change frequency, and priority. While search engines are very good at finding your pages already, the metadata can be particularly useful, as search engines aren't as good at determining the relative importance of pages and how often to check for changes. 

You can find a detailed explanation of the structure of sitemap.xml files and its metadata at the [sitemaps.org](http://www.sitemaps.org/) site.

Once you create the XML file, you can use it for many different search engines. The simplest way to notify search engines about your sitemap.xml file is to include a reference in your robots.txt file. For my site, the entry looks like this: `Sitemap: http://www.kinnetica.com/sitemap.xml`. Google, Yahoo, Bing, and possibly other search engines will then be able to find the sitemap file and use it to help with indexing and crawling all of your pages and posts. 

In addition, by signing up for their respective webmaster tools sites ([Google Webmaster Tools](http://www.google.com/webmasters/tools), [Yahoo Site Explorer](https://siteexplorer.search.yahoo.com), [Bing Webmaster Tools](http://www.bing.com/webmaster)), you can see which of the sites in your sitemap.xml have been indexed by each search engine. With Google Webmaster Tools, you can also let them know when your sitemap.xml has been updated and have them refresh their data.

### Criteria For A Solution

When I started this site, I wanted to automate generating the sitemap.xml file. After reading the documentation on how to create [Jekyll plugins](https://github.com/mojombo/jekyll/wiki/Plugins), I decided to try to write a simple plugin that could generate this file for me.

These were my requirements:

1. It should automatically be able to find all of the posts and pages on my site and provide the URLs.

2. It should be able to automatically figure out the date the page or post was last modified. This is a little tricky, since a change to a layout file could change the output of many files (or possibly all of the posts at once). I decided to take the purist approach and calculated the last modified date by the latest date of either the page or post, or any of the layouts that it uses. However, I might change my mind later and simply use the last modified date of the post.

3. It should provide a way to exclude certain pages and posts if I don't want them in my sitemap.xml file. I am currently only excluding my atom.xml file.

4. It should allow me to manually specify the change frequency and priority for any page or post. By simply providing that information in the YAML Front Matter, the plugin should be able to pick up this information and include it in the generated file.

### Give It A Try

I've completed my first version and wanted to get it out there for people to try. It's currently [available for download](https://github.com/kinnetica/jekyll-plugins) on GitHub. I have provided instructions on how to use it in the README file.

If this seems like it might be useful for you, please give it a try and let me know what you think via [email](mailto:michael@kinnetica.com) or twitter [@kinnetica](http://www.twitter.com/kinnetica).

After all, it's not just the crawlers that can use a little help sometimes.