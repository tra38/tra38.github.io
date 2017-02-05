---
title_bar: Education - Ruby Percentage Constructors
post_title: Ruby "Percentage Constructors"
post_subtitle: Constructors To Make Your Life Easy
layout: default
---
"The Well-Grounded Rubyist" is a very dense and wordy book that covers a lot of Ruby material. One interesting topic that the book covered though is a series of "percentage" constructors designed to make it easier to create arrays and strings. (Disclaimer: David A. Black, the author of "The Well-Grounded Rubyist" did not use such a term in the book. It was a term I made up to classify the constructors that he listed. David A. Black prefers using the more general term "%char".) 

Arrays are useful for storing information, but it can take a lot of time to type them up, make sure they are in the proper format, and ensure that you have commas between each item on a list. "Percentage Constructors" serves as shortcuts that actually will build an array with all items in your list converted to a standard format. No commas are necessary as Ruby will interpret each space as a comma!  Even though these constructors are not entirely intuitive to a code reader, they <em>do</em> save a coder valuable time.

<ul>
<li>%w[list of items]: Creates an array with all items converted to single-quoted strings.</li>
<li>%W[list of items]: Creates an array with all items converted to double-quoted strings (useful because some techinques, like string interpolation, only works with double-quoted strings)</li>
<li>%i[list of items]: Creates an array with all items converted to single-quoted symbols.</li>
<li>%I[list of items]: Creates an array with all items converted to double-quoted symbols (useful when dealing with string interpolation)</li>
</ul>

To use a Percentage Constuctor, you must place it before your list of items you want to be turned into an array. Your list may be surrounded by square brackets - [] - like a normal array, but you could also use also use braces-{} and parentheses-(). Brackets, braces, and parentheses are called "delimiters", since they separate the 'data' into chunks that a program will read. Normally, when you are making an array, you must use square brackets to limit what items are inside the array. But Percentage Constructors are willing to accept other "delimiters" as well.

This means that %W[Cat Dog Penguin], %W{Cat Dog Penguin}, and %W(Cat Dog Penguin) will all produce the same array...["Cat", "Dog", "Penguin"].

<p>Sometimes, you may not want to have Ruby see a space and turn into a comma. In this case, you have to use a backlash character (\) to tell Ruby to treat the space as a character.</p>

For example %W[Tariq Rafiq Ali] will produce the array ["Tariq","Rafiq","Ali"], but %W[Tariq\ Rafiq\ Ali] will produce the array ["Tariq Rafiq Ali"]

Percentage constructors are not only limited to arrays though. They can also be used to make string objects as well.

<ul>
<li>%q[list of items]: Creates a single-quoted string.</li>
<li>%Q[list of items]: Creates a double-quoted string.</li>
<li>%[list of items]: Creates a double-quoted string.</li></ul>

Just like arrays, you do not have to use square brackets. You can use braces or parentheses as well.