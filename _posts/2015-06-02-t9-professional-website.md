---
title_bar: Technical - Wordpress versus Jekyll
post_title: Wordpress versus Jekyll 
post_subtitle: Which One I Prefer?
layout: default
---
Before entering into DevBootCamp, I created websites using Wordpress. During this week of DevBootCamp, we were asked to modify our website to be more professional, using a framework such as Jekyll. So I decided to configure my blog using Jekyll and compare my experience to my year-long-experience with Wordpress, to decide which 'framework' is superior.

Wordpress is a Content Management System: you just upload content, and Wordpress will manage the content for you (by storing and retriving it through databases). By contrast, Jekyll is a "HTML code generator". All it does is take your content and generate web pages out of it, which you can then manually upload directly onto a web server.

Jekyll is rather primitive, but for many people, that's actually a benefit! Wordpress, because of its complexity, is slower than "static HTML pages". Wordpress' databases can also be hacked unless you continually  install all required updates, a rather time-consuming task. When people recommend Jekyll, they do so for these reasons.

Yet, I do not like Jekyll. Wordpress is much more user-friendly, not just in terms of installation (upload it to server, and click a few buttons to allow Wordpress to generate the databases needed to store the data), but also in terms of setting up a website. There is a central repository for website templates and "plugins" built into the software, allowing you to browse through and see what you may want to use. You can preview any changes you make to the website, and push updates immediately. The User-Interface is also very easy to grasp, and no tutorial was necessary.

By contrast, I spent hours reading and re-reading <a href="https://www.andrewmunsell.com/blog/ultimate-jekyll-tutorial">a simple Jekyll tutorial</a> before starting the painful migration process of moving my blog posts into Jekyll. I only was able to succeed through trial and error, and had to continually preview my website by "building" the website again and again so that I can see if there were any changes made.

Jekyll does have helpful commands to help alleviate the pain. I used 'jekyll serve --watch' often so that I can quickly view the results of minor changes and then modify the website. But it did take me a while to find those commands. Documentation was semi-helpful, but I had to also use Google to supplement my knowledge.

Though Wordpress may be much easier to use "out of the box", Jekyll may be much easier to customize. To do any significant changes to Wordpress requires knowledge of both HTML and PHP, while Jekyll only require knowledge of just HTML and "Markdown" (an improved version of plain text). There is some potential for Jekyll, and now that I have gotten the basics of it, I may choose to explore it further. However, if a client wants to set up a website quickly to represent an organization *and plans on running the website himself*, then Wordpress is much more suitable to his goals. If we want people to build well-designed, functioning websites in a reasonable amount of time, then it's clear Wordpress wins, hands-down.

The only praise that I will give to Jekyll is its licensing. Wordpress is licensed under the GPL license, which mandates that any contributions you make to Wordpress (such as producing 'plugins' and themes) must be open-source. This, of course, is no barrier to making money, as people can sell premium plugins/themes and "technical support". But I do have some philosophical objections to the idea of forcing people's contributions to be open-source. Jekyll is licensed under the MIT license, meaning that you can choose to have your contributions to Jekyll be 'closed-source'. I doubt that I would ever make any plugins for Jekyll, but it's nice to know that if I ever do, Jekyll would give me more freedom than Wordpress would.