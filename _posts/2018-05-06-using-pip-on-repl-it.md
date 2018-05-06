---
title_bar: Technical - Using pip on repl.it
post_title: Using Pip on Repl.it
post_subtitle: An Interesting Experience
layout: default
---
>BUILD AND DEPLOY IN SECONDS. Instant programming environment for your favorite language.--[repl.it](https://repl.it)'s homepage

I used repl.it primarly for hosting [LittleNiftySubweb](https://repl.it/@tra38/LittleNiftySubweb), a command-line script that enables me to use [howdoi](https://github.com/gleitz/howdoi) without ever needing to install Python. This is very useful to me since it allows me to easily use howdoi on Windows machines (since Python doesn't come on Windows pre-installed).

Previously, I would need to "package" howdoi as an executable (which usually means bundling howdoi and its dependencies with a Python interperter) on another machine before porting the executable to Windows. This is a very time-consuming process. It also meant that upgrading to the latest version of howdoi would be a pain in the neck, since I have to create a brand new executable.

But on repl.it, all I need to do is to add this line:

```
from howdoi import howdoi # learn more: https://python.org/pypi/howdoi
```

And that's it. repl.it would see if it has a local copy of howdoi, and if it doesn't, download it (and its dependencies) from PyPi. Setup is a breeze...and not only that, but I'm always guaranteed to get the latest version of howdoi from PyPi.

I only need to install howdoi every time repl.it spins up a new instance of the Linux machine for me., and the installation process is pretty quick as well, so I can go straight into using the package.

```
Repl.it: Installing fresh packages
Repl.it: howdoi

Collecting howdoi
   Downloading https://files.pythonhosted.org/packages/bc/21/87dd3caacaa7c
   372a9838de8e2a2a9640043e72f382cf1300574e78e9a86/howdoi-1.1.13.tar.gz
Collecting pyquery (from howdoi)
  Downloading https://files.pythonhosted.org/packages/09/c7/ce8c9c37ab8ff8
  337faad3335c088d60bed4a35a4bed33a64f0e64fbcf29/pyquery-1.4.0-py2.py3-none-any.whl

...

Successfully installed certifi-2018.4.16 chardet-3.0.4 cssselect-1.0.3
howdoi-1.1.13 idna-2.6 lxml-4.2.1 pygments-2.2.0 pyquery-1.4.0
requests-2.18.4 requests-cache-0.4.13 urllib3-1.22
You are using pip version 9.0.1, however version 10.0.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
```

However, this system only works if the package you want to install exists on PyPi. What if you wanted to install a package from another source, like GitHub?

I realized this issue when I forked howdoi, created a branch (```links```), and made some changes before [submitting a pull request](https://github.com/gleitz/howdoi/pull/197). I wanted to test out my changes in a production environment while waiting for the PR to approved, but I didn't want to deploy my minor fork onto PyPi -- the fork would be renderered useless once the PR is approved and merged.

I created an experimental fork of "LiftyNiftySubweb"...called [LittleNiftySubweb-Experimental](https://repl.it/@tra38/LittleNiftySubweb-Experimental) (really, creative name, I know), and then started tinkering with that fork, trying to see if I can get my version of howdoi loaded onto their system.

I remembered that pip does have an option to install a Python package from git. For example...

```
pip install git+https://github.com/example_user/example_repo.git
```

By default, pip selects the master branch to install from, but you can also specify what branch you want to install from.

```
pip install git+https://github.com/example_user/example_repo.git@example_branch
```

So all I have to do is to call pip with the proper command-line arguments (providing the link to my repo along with the the name of my branch) and it'll all be set.

However, you do not have access to repl.it's Linux instance directly. Instead, the only way you can access the instance and run commands like pip is through the programming environment. Which didn't take too long to figure out.

```
def install(package):
  import pip
  pip.main(['install', package])

install("git+https://github.com/tra38/howdoi.git@links")
```

However, running this command revealed a very interesting error:

```
Collecting git+https://github.com/tra38/howdoi.git@links
  Cloning https://github.com/tra38/howdoi.git (to links) to /tmp/pip-vtyex9f7-build
  Error [Errno 2] No such file or directory: 'git' while executing command git clone -q https://github.com/tra38/howdoi.git
```

It is surprising to me that repl.it's Linux instance doesn't come pre-installed with git. I don't know if it was meant to save space or if it was just an oversight on their part. Trying to programatically install git on their machine using a simple Python shell didn't seem doable, so instead I explored other options.

A simple StackOverflow search later and I learned that GitHub also [packages up its repos as zipball or tarball files](https://developer.github.com/v3/repos/contents/#get-archive-link) (with each zip file referring to a valid "reference", usually the name of a branch of the git repo). All I have to do is to directly provide a link to the archive that I want to download. pip can then read that archive.

```
def install(package):
  import pip
  pip.main(['install', package])

install("https://github.com/tra38/howdoi/zipball/links")
```

This works...sorta. I was able to download howdoi package and its dependencies, but installing these packages and dependencies lead to a permissions issue.

```
Collecting https://github.com/tra38/howdoi/zipball/links
  Downloading https://github.com/tra38/howdoi/zipball/links
Collecting pyquery (from howdoi==1.1.13)
  Downloading https://files.pythonhosted.org/packages/09/c7/ce8c9c37ab8ff8
  337faad3335c088d60bed4a35a4bed33a64f0e64fbcf29/pyquery-1.4.0-py2.py3-
  none-any.whl

...

PermissionError: [Errno 13] Permission denied: '/usr/local/lib/python3.6/site-packages/cssselect-1.0.3.dist-info'
```

One way to get around that permissions issue is to use ```sudo```, but when you use ```sudo```, you need to type in a password, and I don't know what is the password for the Linux machine. Besides, using ```sudo``` is considered bad practice when using pip. Instead, I decided to specify that I want to install this packages into my own user directory, by using the ```--user``` command-line option.

```
def install(package):
  import pip
  pip.main(['install', package, "--user"])

install("https://github.com/tra38/howdoi/zipball/links")
```

Installation was now successful.

```
Collecting https://github.com/tra38/howdoi/zipball/links
  Downloading https://github.com/tra38/howdoi/zipball/links
Collecting pyquery (from howdoi==1.1.13)
  Downloading https://files.pythonhosted.org/packages/09/c7/ce8c9c37ab8ff8
  337faad3335c088d60bed4a35a4bed33a64f0e64fbcf29/pyquery-1.4.0-py2.py3-
  none-any.whl

...

Installing collected packages: cssselect, lxml, pyquery, pygments, requests-cache, howdoi
  Running setup.py install for howdoi ... done
  Successfully installed cssselect-1.0.3 howdoi-1.1.13 lxml-4.2.1 pygments
  -2.2.0 pyquery-1.4.0 requests-cache-0.4.13
You are using pip version 9.0.1, however version 10.0.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
```

But then when I try to use the howdoi module from that same script...

```
Traceback (most recent call last):
  File "main.py", line 33, in <module>
    from howdoi import howdoi
ModuleNotFoundError: No module named 'howdoi'
exit status 1
```

When I "run" my script again, I get something even more surprising.

First, I *was* able to import the howdoi module (and could successfully use my version of howdoi). [This answer](https://stackoverflow.com/questions/32478724/cannot-import-dynamically-installed-python-module) from StackOverflow explains kinda what happened.

>If a path that does not yet exist is added to sys.path, it doesn't seem like it will ever be checked again when importing modules, even if it exists at a later point (or at least in python 2.7).

repl.it's Linux instance is using Python 3.6.1, so I believe that this behavior has not changed.

Second, howdoi attempts to install a bunch of packages that I never even asked to be installed!

```
Repl.it: Installing fresh packages
Repl.it: BeautifulSoup, Pillow, Sphinx, beautifulsoup4, colorama, ctags, docutils, html5lib, pkg_resources, pymongo

Collecting BeautifulSoup
  Downloading https://files.pythonhosted.org/packages/1e/ee/295988deca1a5a
  7accd783d0dfe14524867e31abb05b6c0eeceee49c759d/BeautifulSoup-3.2.1.tar.
  gz
    Complete output from command python setup.py egg_info:
    Traceback (most recent call last):
      File "<string>", line 1, in <module>
      File "/tmp/pip-build-b4z379k2/BeautifulSoup/setup.py", line 22
        print "Unit tests have failed!"
                                      ^
    SyntaxError: Missing parentheses in call to 'print'

    ----------------------------------------
Command "python setup.py egg_info" failed with error code 1 in /tmp/pip-build-b4z379k2/BeautifulSoup/
You are using pip version 9.0.1, however version 10.0.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.
```

But, let's ignore BeautifulSoup and focus on howdoi here. I rewrote the code, following the advice from [this SO answer](https://stackoverflow.com/questions/32478724/cannot-import-dynamically-installed-python-module).

```
# https://stackoverflow.com/questions/32478724/cannot-import-dynamically-installed-python-module
def set_up_user_directory():
  import os
  import sys
  import site
  # this makes it work
  if not os.path.exists(site.USER_SITE):
    os.makedirs(site.USER_SITE)
    # since I'm installing with --user, packages
    # should be installed here,
    #so make sure it's on the path
    sys.path.insert(0, site.USER_SITE)

def install(package):
  # set_up_user_directory()
  import pip
  pip.main(['install', package, "--user"])
```

But this wound up not working properly at all, since repl.it decided to automatically ignore my configuration, preferring instead to install the latest version of howdoi from PyPi (rather than my version of howdoi)!

```
Repl.it: Installing fresh packages
Repl.it: howdoi

Collecting howdoi
  Downloading https://files.pythonhosted.org/packages/bc/21/87dd3caacaa7c3
  72a9838de8e2a2a9640043e72f382cf1300574e78e9a86/howdoi-1.1.13.tar.gz
```

But you know what, I'm already fine with waiting for repl.it to download  packages anyway (as you can see with my total disregard for the random package download of BeautifulSoup). With that in mind, I finally deduced a ~~elegant~~ hacky approach to the problem I'm facing.

Here it is.

```
# https://stackoverflow.com/questions/32478724/cannot-import-dynamically-installed-python-module
def set_up_user_directory():
  import os
  import sys
  import site
  # this makes it work
  if not os.path.exists(site.USER_SITE):
    os.makedirs(site.USER_SITE)
    # since I'm installing with --user, packages
    # should be installed here,
    #so make sure it's on the path
    sys.path.insert(0, site.USER_SITE)

def install(package):
  set_up_user_directory()
  import pip
  pip.main(['install', package, "--user", "--upgrade"])

install("https://github.com/tra38/howdoi/zipball/links")
```

When I run the script, repl.it first installs the latest version of howdoi from PyPi...

```
Repl.it: Installing fresh packages
Repl.it: howdoi

Collecting howdoi
  Downloading https://files.pythonhosted.org/packages/bc/21/87dd3caacaa7c3
  72a9838de8e2a2a9640043e72f382cf1300574e78e9a86/howdoi-1.1.13.tar.gz

...

Successfully installed certifi-2018.4.16 chardet-3.0.4 cssselect-1.0.3
howdoi-1.1.13 idna-2.6 lxml-4.2.1 pygments-2.2.0 pyquery-1.4.0
requests-2.18.4 requests-cache-0.4.13 urllib3-1.22
You are using pip version 9.0.1, however version 10.0.1 is available.
You should consider upgrading via the 'pip install --upgrade pip' command.


Repl.it: package installation success
```

Then, it runs the ```set_up_user_directory()``` function to create a user directory and to add it to ```sys.path```.

...and then it runs my commands to "upgrade" howdoi - thereby replacing the PyPi version of howdoi with *my* version of howdoi (located within a user directory that I have permissions for).

```
Collecting https://github.com/tra38/howdoi/zipball/links
  Downloading https://github.com/tra38/howdoi/zipball/links

...

Installing collected packages: howdoi, certifi
  Running setup.py install for howdoi ... done
  Successfully installed certifi-2018.4.16 howdoi-1.1.13
```

And only *then* I can use my version of howdoi.

The only catch is that every time I run the script, I will still re-install my version of howdoi, even if I already have it installed on the Linux instance.

```
Collecting https://github.com/tra38/howdoi/zipball/links
  Downloading https://github.com/tra38/howdoi/zipball/links

...

Installing collected packages: howdoi
  Found existing installation: howdoi 1.1.13
    Uninstalling howdoi-1.1.13:
      Successfully uninstalled howdoi-1.1.13
  Running setup.py install for howdoi ... done
Successfully installed howdoi-1.1.13
```

So I will have to wait longer to use my script. I think it's a fair trade-off though. Eventually, once my changes get merged into master, I can give up my experimental version.

If you like to try out the experimental version of howdoi for yourself, you can click on [this link](https://repl.it/@tra38/LittleNiftySubweb-Experimental).

<hr>

I think this entire experience is another good illustration of the [Generalized Peter Principle](https://en.wikipedia.org/wiki/Peter_principle): "Anything that works will be used in progressively more challenging applications until it fails." repl.it was very useful for me, so useful that I eventually encountered a serious problem with it.

I previously faced the Generalized Peter Principle before in [A Real-World Example Of "Duck Typing" In Ruby](http://tra38.github.io/blog/t19-ruby-duck-typing.html), and vowed to be "more cautious and careful when programming" next time.

But maybe being "more cautious and careful" is not possible in the real world. When you encounter a useful tool, you get lulled into a false sense of security (because the tool worked so well *before*)...which eventually lead to you encountering a serious challenge. I'll have to think of a better approach to dealing with the Generalized Peter Principle.