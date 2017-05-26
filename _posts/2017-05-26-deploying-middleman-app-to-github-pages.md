---
title_bar: Technical - Middleman Deployment
post_title: How To Abuse the /docs "Feature" To Quickly Deploy a Middleman Static Site Onto GitHub Pages
post_subtitle: A Hacky Solution
layout: default
---

>"Middleman is a static site generator using all the shortcuts and tools in modern web development."---[Middleman Home Page](middlemanapp.com)

One of those shortcuts is having a directory structure to help organize your project. Here's a short version of that directory structure (a more complete version is located in [the docs](https://middlemanapp.com/basics/directory-structure/)).

~~~
mymiddlemansite/
-- .gitignore
-- Gemfile
-- Gemfile.lock
-- config.rb
-- source (all the files necessary for building the static site)
-- build (the generated static site files)
~~~

The idea is that you would write all your code in the source directory, type in ``bundle exec middleman build`` to generate your build directory, and then ship this build directory elsewhere to be served by a web server. Most likely, you would use a tool such as [middleman-deploy](https://github.com/middleman-contrib/middleman-deploy) or [middleman-gh-pages](https://github.com/edgecase/middleman-gh-pages) to automate the deployment process. Both of these tools are able to natively support deploying to GitHub Pages, usually by pushing up the build directory to the ``gh-pages`` branch of a GitHub repository.

But what if you don't want to use those tools to deploy to a separate branch of your repository? What if you wanted your website files to be in the **same** branch as your Middleman source code, for maintainability and aesthetic reasons? GitHub Pages luckily gives you that option...though in a rather indirect and hacky fashion.

![Three Options: gh-pages branch, master branch, or /docs](https://help.github.com/assets/images/help/pages/select-gh-pages-or-master-as-source.png "Logo Title Text 1")

In the settings of your GitHub repository, you tell GitHub Pages to read from either the ```gh-pages``` branch, the ```master``` branch, or the ```/docs``` folder.

The last option is incredibly useful for open-source projects who wants a specific ```/docs``` folder to store all their documentation files for their projects. For example, the [Classifier-Reborn open source project](https://github.com/jekyll/classifier-reborn) has a [GitHub Page](http://www.classifier-reborn.com), and its source code is stored within the [```/docs``` folder](https://github.com/jekyll/classifier-reborn/tree/master/docs).

So we're going to abuse this feature to deploy our own Middleman site. First, we need to select the ```master branch /docs folder``` option in the settings of our repo. Second, we need to rename  ```/build``` to ```/docs```. This can be done by editing ```config.rb``` to change the build directory's name.

~~~
configure :build do
  set :build_dir, 'docs'
~~~

Finally, we just type out...

~~~
bundle exec middleman build
~~~

...commit the resulting build folder to our repository, and then push the result up to our GitHub repository.

There is still one tiny flaw though. Any time you need to make a change, you must rebuild the ```/docs``` directory and commit the generated files. I leave it to the reader to decide how to best automate this process (probably by writing out a Raketask).