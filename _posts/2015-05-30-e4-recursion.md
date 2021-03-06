---
title_bar: Education - Recurison
post_title: Recursion
post_subtitle: A Simple Explaination of a Simple Example (in Ruby)
layout: default
---
Tim Cannaday, a fellow student at DevBootCamp, <a href="https://timcannady.github.io/blog/blog_posts/t8-tech.html">wrote a blog post about various technical issues</a>, including recurison. He showed an example of recurison in action by using it to calcuate Fibonnaci Numbers...except that, er, Tim Cannady didn't understand it.

*[I] don't really understand what fibonacci() is doing.*---Tim Cannady

As a way of thanking Tim for his example, I'll...uh...explain his example? Please forgive me if this explaination isn't exactly elegant: the goal is to explain, not to do so prettily.

This was the code that Tim used:

~~~
def fibonacci(n)
n <= 1 ? n : fibonacci(n-1) + fibonacci(n-2)
end

p fibonacci(12)
#=>144
~~~

<p>And here is what the code is actually doing in IRB:</p>

<code>
*<strong>Stack 1: fibonacci(12)</strong>: Okay, first thing I should do, check to see if 12 is less than or equal to 1. If 12 is less than or equal to 1, I just output 12, and I'm good to go.
</code>

<code>
Wait. 12 <em>isn't</em> less than or equal to 1? Okay, then, new plan. I'll just return fibonacci(12-1) + fibonnacci(12-2)...which is, fibonnaci(11)+fibonnaci(10).
</code>

<code>
All I have to is to create two new stacks: fibonnaci(11) and fibonnaci(10). I'll just ask them to return their values over to my stack, and I can then plug them into the equation and return the answer. Simple.
</code>

<code>
I'll just wait until those two functions are done...
</code>

<code>
<strong>Stack 2: fibonacci(11)</strong>: Awesome! Thanks Stack 1. Okay, I should first check to see if 11 is less than or equal to 1. If 11 is less than or equal to 1, I just return 11 to Stack 1, and I'm good to go.
</code>

<code>
Wait. 11 <em>isn't</em> less than or equal to 1? Okay, then, new plan. I'll just return fibonacci(11-1) + fibonnacci(11-2)...which is, fibonnaci(10)+fibonnaci(9).
</code>

<code>
All I have to is to create two new stacks: fibonnaci(10) and fibonnaci(9). I'll just ask them to return their values over to my stack, and I can then plug them into the equation and return my answer over to Stack 1. Simple.
</code>

<code>
I'll just wait until those two functions are done...
</code>

<code>
<strong>Stack 3: fibonacci(10)</strong>: What do you mean that 10 is not less than or equal to 1? That means I have to now create two new stacks (fibonnaci(9) and fibonacci(8) ) and wait for them to be done.
</code>

<p>Several stacks later...</p>

<code>
<strong>Stack 11: fibonacci(3)</strong>: Yay! Stack 10 (currently handling a difficult puzzle of fibonacci(4) ) have just created me to help him with his very important Fibonacci. And, lo and behold, 3 is not less than or equal to 1. I'll have to return fibonnaci(2)+fibonnaci(1). Time to create some new stacks...and then wait excitedly for the results!
</code>

<code>
<strong>Stack 12: fibonacci(2)</strong>: Well, 2 is not less than or equal to 1. So I'm going to have to create two new stacks: fibonnaci(1), and fibonnaci(0), and then wait for their results. Once I get their results, I'll add them up and return the answer to you, Stack 11.
</code>

<code>
<strong>Stack 13: fibonacci(1)</strong>:  Okay, first thing I should do, check to see if 1 is less than or equal to 1. If 1 is less than or equal to 1, I just return 1. <strong>Oh cool!</strong> 1 is less than or equal to 1! I'll just return 1 over to Stack 13!
</code>

<code>
<strong>Stack 14: fibonacci(0)</strong>: <strong>Oh cool!</strong> 0 is less than or equal to 1! I'll just return 0 over to Stack 13!
</code>

<code>
<strong>Stack 12:</strong> Alright, so Stack 13 returned 1 and Stack 14 returned 0. 1+0 is equal to 1. Stack 11, here's your answer: 1!
</code>

<code>
<strong>Stack 11: fibonacci(3)</strong>: Good, Stack 12 is done. So, now that I know that fibonacci(2) is equal to 1. So whatever fibonnaci(1) is equal to, I just add 1 to it and then return it over to Stack 10. Let's see how Stack 15 is doing...
</code>

<code><strong>Stack 15: fibonacci(1)</strong>: <strong>Oh cool!</strong> 1 is indeed less than or equal to 1! I'm done. I return 1 over to Stack 11!</code>

<code><strong>Stack 11</strong>: Excellent. 1+1 is equal to 2! I can return this value over to Stack 10, who will then use this value to help him calcuate fibonnaci(4). I love my job.</code>

<p>Moving back up the stacks...</p>

<code>
<strong>Stack 3: fibonacci(10)</strong>: According to the stacks that I have created (and the stacks they have created, and the stacks <em>they</em> have created, etc.), fibonnaci(9) is equal to 34 and fibonacci(8) is equal to 21. 34+21=55. I'll return the value of 55 over to Stack 2.
</code>

<code>
<strong>Stack 2: fibonacci(11)</strong>: According to the stacks, fibonnaci(10) is equal to 55 and fibonacci(9) is equal to 34. 55+34=89. I'll return the value of 89 over to Stack 1.
</code>

<code>
<strong>Stack 1: fibonacci(12)</strong>: According to the stacks, fibonnaci(11) is equal to 89 and fibonacci(10) is equal to 55. 89+55=144. I'll return 144 as the final answer.
</code>

<code>
...that was slow.
</code>

And Stack 1 is right. Recurison is much slower than other approaches, such as simple looping, because you are creating all these stacks. However, recurison is sometimes easier to code and understand! Some problems are very easy to solve using recursion (such as the "Tower of Hanoi" problem), but are incredibly complex when you are trying to do a simple loop. And since computers continue to increase in processing power and speed, the "slowness" of recurison is usually a cost many programmers are willing to pay. Nobody is really going to care about losing a few milliseconds.
