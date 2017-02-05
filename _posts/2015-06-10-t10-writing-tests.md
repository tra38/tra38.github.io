---
title_bar: Technical - What Tests You Should Delete?
post_title: What Tests Should You Delete
post_subtitle: Advice from POODR On Pruning
layout: default
---
Testing is an important part of any programmer's life, to detect and eliminate bugs. But writing automated tests themselves can be rather costly endeavour. Not only does it take time to write your tests, but you also must make sure your tests are working properly as well. To reduce your costs, you need to reduce the amount of tests you write.

According to the [Practical Object-Oriented Guide to Ruby](poodr.com), automated tests should only test the *outputs* of your code. Trying to test **how** that code calcuates the output would lead to your tests breaking every time you change that code. This will waste a lot of time and energy that could be spent on other aspects of your programs. Just test the outputs of a program.

POODR also suggests that you should check to see if this output ever actually gets used anywhere in the program or displayed to the user. If nobody (not even the code) gets to see this output, then it's possible that this output is unncessary. You can then delete the code that produces the output without fear, and will not have to worry about testing this code as well. You have saved yourself time and grief in maintaining the code that produces your output.

Finally, POODR recommends not testing private methods. Private methods are methods that you want only the computer program to use. Since you do not want any human using them, you are free to not test these methods. It can be assumed that the program will end up using those private methods to calcuate the outputs, and if the private methods are bugged, then the resulting outputs would be wrong as well. Then the tests that you have written will indicate to you that a bug exists in your code, and you can then fix the private methods in question.

I wrote a blog post recently on the differences between [automated testing and manual testing](/blog{% post_url 2015-05-28-t8-tech %}). One of the points I made is how automatic tests are more efficent than manual testing but are also more expensive to create. By reducing the number of tests you create, you reduce your costs, and thereby benefit more from automated testing.