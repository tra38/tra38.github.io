---
title_bar: Technical - Cycle Method
post_title: .Cycle In Ruby
post_subtitle: What is it? And how do you use it?
layout: default
---
**Enumerable#cycle** - "Calls block for each element of enum repeatedly n times or forever if none or nil is given." (<a href="http://ruby-doc.org/core-2.1.0/Enumerable.html#method-i-cycle">Rubydocs</a>) If this definition sounds confusing, don't worry, this essay will explain it.

Understanding what Enumerable#cycle (or .cycle) does in Ruby requires you to understand Enumerable#each (or .each).

.each will grab each item within an array and shove it into a 'block' (code placed within brackets). For example:

<code>example_array = [0,1,2]

example_array.each { |x| puts x*2 }

=>0, 2, 4
</code>

But what if I wanted to use .each multiple times? Well, you would use .cycle instead!

<code>
example_array.cycle(2) { |x| puts x*2 }

=>0, 2, 4, 0, 2, 4
</code>

You must specify a number for .cycle , otherwise, Ruby will not know when to stop.

<code>
example_array.cycle { |x| puts x*2 }

=>0, 2, 4, 0, 2, 4, 0, 2, 4, 0, 2, 4, 0, 2, 4...

And so on...for infinity.
</code>

...Sometimes, you may want an endless sequence like this. If you want only see one number at a time in this endless sequence, you will need to save "example_array.cycle" in a variable, and then use the '.next' method on that variable.

<code>
nextnumber = example_array.cycle { |x| puts x*2 }

nextnumber.next => 0

nextnumber.next => 2

nextnumber.next => 4

nextnumber.next => 0

nextnumber.next => 2

And so on...for infinity.
</code>