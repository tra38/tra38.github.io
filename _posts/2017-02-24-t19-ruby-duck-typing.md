---
title_bar: Technical - Ruby Duck Typing
post_title: A Real-World Example Of "Duck Typing" In Ruby
post_subtitle: Or, an Illustration of the Generalized Peter Principle
layout: default
---
"Duck-typing" is a very useful tool in Ruby. But sometimes, tools break. Every tool is useful, until the day the tool stops being useful, and it's time to do some debugging...

~~~ ruby
def get_first_element(object)
    object[0]
end
~~~

Here, I defined a Ruby method that will take any arbitrary object and call the [] method on it.

Now, normally you call the [] method on an array, so this method tends to work as expected with arrays.

~~~ruby
array = [1,2,3]
get_first_element(array)
#=>1
~~~

But it doesn't just handle arrays. In fact, it handles any arbitrary object that responds to the [] method.

~~~ruby
string = "Alphabet"
get_first_element(string)
#=>"A"
~~~

As long as the object responds to the [] method, that's good enough for me. And that is the basis of **duck typing**. It is based on the principle that if an element 'quacks like a duck', it is therefore a duck. If it quacks like an array, it is an array. And if I pass in an object that doesn't support the [] method, we'd simply see an error raised, like so...

~~~ruby
awesome_object = Object.new
get_first_element(awesome_object)
#=>NoMethodError: undefined method `[]' for #<Object:0x007f9a93135b70>
~~~

The error message is probably most helpful for the programmer who has access to the source code of ```get_first_element```, but at least the program halted at execution.

And that's all I have for now. I'll leave you with these cool code snippets of me getting the first element of integers. Happy coding.

~~~ruby
integer = 1
get_first_element(integer)
#=>1
~~~

Uh...

~~~ruby
get_first_element(2)
#=>0

get_first_element(30)
#=>0
~~~

Cancel the happy coding.

Integers in Ruby *also* respond the [] method. [According to the docs](http://www.rubydoc.info/stdlib/core/Fixnum:%5B%5D), integers appear to have a binary representation "under the hood", and the [] method gets me the ```n```th digit of that binary representation. The docs give a pretty good example of what's going on...

~~~ruby
#Define a as the integer 13098, by using its binary representation
a = 0b11001100101010

#Retrieve that same binary representation by using []
30.downto(0) { |n| print a[n] }
#=> 0000000000000000011001100101010
~~~

After all, all numbers must have a binary representation, and that binary representation has to be stored somewhere, and you might as well treat that stored binary representation as an array. It sounds like completely expected behavior so long as you know to expect it in advance.

The duck has quacked, and so we assume it to be a duck. And it *is* a duck...don't get me wrong. Just a duck that I was unfamiliar with.

Coincidentally, I actually used ```get_first_element``` in a personal side-project. I stayed up all night trying to track down weird bugs that occurred when I was passing integers into ```get_first_element```. Once I realized what was causing this, I added a quick hotfix to solve the issue...

~~~ruby
def get_first_element(object)
    string = object.to_s
    string[0]
end
~~~

Call the object's ```to_s``` method, thereby creating a string representation of the object. Then, simply access the first element of that string. This meant that ```get_first_element``` handled integers as I **wanted** them to...

~~~ruby
get_first_element(1)
#=>"1"

get_first_element(2)
#=>"2"

get_first_element(30)
#=>"3"
~~~

...but now users will be surprised at how the method handles arrays.

~~~ruby
[1,2,3].to_s
#=>"[1,2,3]"

get_first_element([1,2,3])
#=>"["
~~~

And objects that would previously raise an error under the old ```get_first_element``` would now produce a "valid" result under the new ```get_first_element```, if the objects are able to "quack" (respond to the ```to_s``` method)...

~~~ruby
awesome_object = Object.new

awesome_object.to_s
#=> "#<Object:0x007f9a9314f3e0>"

get_first_element(awesome_object)
#=>"#"
~~~

Luckily for me, the personal side-project only dealt with strings and integers. If my side-project ever had to support arrays or other arbitrary objects though (which is always a possibility, considering how often software changes), I would probably consider:

 - Writing a lot of ugly and overly-complex code to get ```get_first_element``` to behave as I intended it to (formalizing my beliefs about how the method is "supposed" to work through automated tests).
 - Writing documentation explaining and **justifying** all the quirks. Saying, "This is how it works, deal with it" just won't fly.
 - Eliminating ```get_first_element``` entirely and rewriting the side-project.

I dread having to take any of these approaches. If forced to choose though, I would pick "rewriting the side-project". My side-project was using ```get_first_element``` to do some rather "hacky" stuff, and there's probably a much better (and less painful) way to do that same stuff. All I have to do is find it...and then implement it.
<hr>
This post is not an attack against duck-typing, although my reliance on duck-typing did lead to this error. Duck-typing is part of idiomatic Ruby, and taking advantage of it tends to lead to "cleaner" code. But there are always trade-offs to consider, such as the ducks doing behaviors that you didn't intend them to simply because the ducks knew how to quack. But I never even experienced these trade-offs -- until now.

This blog post was really an illustration of the [Generalized Peter Principle](https://en.wikipedia.org/wiki/Peter_principle): "Anything that works will be used in progressively more challenging applications until it fails." Generally, this principle is usually applied to human beings -- "Workers rise to their level of incompetence." Duck-typing is useful, and it is precisely that it was so useful that it led me to spend the whole night debugging an issue caused by my use of duck-typing.

I'm still going to use duck-typing. It's just too useful and convenient, and the odds of me encountering this issue in another Ruby side-project seems fairly low.

But I'm going to be more cautious and careful when programming. More importantly, I plan to be more comfortable with my ignorance...never assuming that I know more than I actually do about the program I am writing, the patterns that I am using when writing the program, the language I am writing the program in, and the requirements that I am writing the program for.

Being comfortable with ignorance means that I might be able to anticipate and prepare for situations where the Generalized Peter Principle comes true and my tools break hard.

 *Note* - This article was originally published on [dev.to](https://dev.to/tra/a-real-world-example-of-duck-typing-in-ruby/) on Feb. 21st 2016, and has since ported over here.