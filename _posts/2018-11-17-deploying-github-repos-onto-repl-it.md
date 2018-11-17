---
title_bar: Technical - Deploying GitHub Repos onto repl.it
post_title: Deploying GitHub Repos onto repl.it
post_subtitle: Easier Than Expected
layout: default
---
repl.it is a very useful tool for distributing code snippets for other people to use.

But sometimes, you may want to use repl.it to distribute entire GitHub repositories (not just a single script). You could just drag-and-drop your GitHub repo, but that's not a sustainable solution - it would only be a snapshot of the code, not the *latest* version of your repo. What you actually  need is a solution that automatically fetches the latest version of your code and run it in repl.it's Virtual Machine.

It's actually fairly easy to do that (deploying a GitHub repo onto repl.it).  You need to write a script that does the following:

1. Remove the existing folder, in case you already cloned it down before. You want to ensure you have downloaded the latest version of the code.
2. ```git clone``` the repo (ensuring that you have got the latest code).
3. Run the code (or come up with a terminal prompt to allow users to decide what code to run).

I wound up needing to write this sort of script when deploying a Ruby side-project of mine ([Paranoia Super Mission Generator](https://github.com/tra38/Paranoia_Super_Mission_Generator)) onto [repl.it](ttps://repl.it/@tra38/PARANOIASuperMissionGenerator).

I suppose it makes sense for this to be a ```bash``` script, but I couldn't really get that to work due to (a) not being able to run ```ruby```, and (b) lacking permissions to run files directly (which kinda ruins the point of using bash). So I wrote this as a Ruby script, though it does call some bash commands as approriate. Here's how Step 1 and Step 2 worked:

```ruby
%x{ rm -rf Paranoia_Super_Mission_Generator }
%x{ git clone https://github.com/tra38/Paranoia_Super_Mission_Generator }
```

Step 3 can be a bit challenging though, and may be somewhat dependent on the type of language you're using. I'll just tell you how I did it in Ruby.

First, repl.it doesn't support requiring Ruby gems all that well, and require us to use ```bundler/inline``` instead of a Gemfile to install dependencies. Here's [repl.it's blog post on the issue](https://repl.it/site/blog/ruby_gems), and [a tutorial on using ```bundler/inline```](https://gist.github.com/chrisroos/0ddf618ac711abe0f465). I could easily add the ```bundler/inline``` boilerplate within the deployment script though, so it's not that big of a challenge (and doesn't require me to change my GitHub repo code at all).

```ruby
require 'bundler/inline'

gemfile true do
 source 'http://rubygems.org'
 gem "calyx", '>=0.18.0'

 gem "ruby-lzma"

 gem "redcarpet"

 gem 'progressbar'
end
```

Once these dependencies are installed, then you can ```require``` Ruby gems without any issues.

Second, due to permission issues, I could not use a command like ```./Paranoia_Super_Mission_Generator/main.rb``` to run ```main.rb```. However, Ruby does have a command called ```load```, which allows us to load any arbitrary Ruby file. This circumvents the permissions file.

As a bonus, you can call ```load``` multiple times, meaning you can rerun the same Ruby file over and over. This means I could build a menu that allow users to pick whatever Ruby file they want to run (and be able to re-run that same Ruby file without any penalty).

Here's how I wrote the code to implement this menu:

```ruby

def menu
  puts "Welcome to PARANOIA Super Mission Generator. For instructions and guidance, please visit https://github.com/tra38/Paranoia_Super_Mission_Generator"
  puts "1 - ``main.rb`` (generate a mission based on a title)"
  puts "2 - ``railroad.rb`` (generate a mission based on a search term you want)"
  gets
end

def main
  load 'Paranoia_Super_Mission_Generator/main.rb'
  puts ""
  puts "Press enter to continue"
  gets
end

def railroad
  load  'Paranoia_Super_Mission_Generator/railroad.rb'
  puts ""
  puts "Press enter to continue"
  gets
end

while (true)
  input = menu.to_i

  if input == 1
    main
  elsif input == 2
    railroad
  else
    puts "Input invalid. Please...try again."
  end

end
```

Appendix Note:

Last time when I [blogged about repl.it](https://tra38.github.io/blog/using-pip-on-repl-it.html), repl.it did not support ```git```, requiring me to download a "zip" version of my code instead. Today, though, repl.it does support git, so this is very handy and convinent. If repl.it didn't support ```git``` though, I could still attempt to download a zipped file of my code, unzip it, and then run the unzipped codebase.

There are always multiple ways to solve the same problem.