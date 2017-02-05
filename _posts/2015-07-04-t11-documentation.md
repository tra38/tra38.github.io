---
title_bar: Technical - Documentation
post_title: An Intro to Documentation
post_subtitle: 4 Ways To Explain Your Code
layout: default
---
If you are given a powerful program, but are not given the instructions on how to use it, then the program is worthless to you. Documentation is essential to understanding code.

Yet, documentation is neglected in the programming community. Many people tend to prioritize producing quality code over writing out how the code is supposed to work. While this may seem sensible in the short-term, in the long-term, it leads to code that is difficult for people to use. Many prospective programmers will be scared off by the complexitiy of the code, and the few that remain will spend valuable time understand what the program does instead of actually improving it.

The most common form of documentation is 'human-readable paperwork'. Examples of such paperwork includes READMEs, flowcharts, diagrams, technical manuals, and code comments. This sort of documentation is useful for people to understand the code quickly (provided the paperwork itself is well-written). However, the documentation can quickly become obsolete whenever a new update to the program is released. As a result, such documentation must be updated constantly for it to be useful. The constant strain of updating "human-readable paperwork" is a major reason why people tend to fear documentation altogether.

But documentation is still necessary. So programmers have been exploring *alternatives* to human-readable paperwork. These alternatives are tied directly to the source code, so whenever the code is updated, the documentation is too. These alternatives include tests, names, and self-documenting code. 

1) Automated tests can inform programmers about about how the code is supposed to behave. By running the tests, you can learn whether the program actually does end up behaving as it is supposed to. Since automated tests are more effective at debugging than manual testing, programmers are encouraged to have these tests anyway. So the "documentation" is seen as a 'bonus'. Automated tests however only tell you what code is supposed to do, and not *why*. You also have to still write the tests in question, and write enough tests to convey all that is essential to know about the program.

2) Names convey information about a particular section of code. Whether you are naming a variable (list_of_dogs), a method (add_dog_to_list), or even a class (List), you are sending a message about what that code does (and usually more quickly than you would with a comment). Knowing what the code is supposed to do helps someone also understand how the code is supposed to work as well. However, it is extremely difficult to name variables properly and what seems like a clear variable name to the original programmer may not be to future programmers.

3) Self-documenting code refers to having a consistent "style guide" within the code proper and ahdering to it. If a programmer is familiar with the 'coding conventions' that the "style guide" promotes, then the programmer is better able to understand the program. There are innumerable style guides for every language though, so someone who is not familiar with the conventions of your guide may struggle with understanding the code. It may be difficult to convince all programmers on the team to follow the chosen "style guide" properly.

Of course, ideally, a programmer would want all types of documentation: human-readable paperwork, automated tests, names and self-documenting code. The problem is that documentation takes time to produce, and skill to produce **well**. It is essential to have good documentation, but there are many ways to do it, and some programmers will naturally graviate towards some forms of documentation while shying away from others.

<!-- It is tempting to also have tests also play a secondary role of informing people about the code tends to be 

 "self-documenting code": code that is easy for programmers to understand. The two parts of self-documenting code are variable names and automated testing.

Variable names can also serve as documentation. Variable names help to explain what is the purpose of the 'variable' in the program. However, it is extremely difficult to name variables properly and 
 -->