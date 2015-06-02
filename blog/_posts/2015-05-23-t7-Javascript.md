---
title_bar: Technical - Objects in JavaScript and Ruby
post_title: Objects in JavaScript and Ruby
post_subtitle: The Difference Between The Langauges
layout: default
---
*Object - "code that can contains both data (information/attributes) and behavior (methods). You can give objects information to hold, while also telling objects to "do" certain stuff." (Source: <a href="t6-oop-concepts.html">OOP Concepts blog post</a>)*

Ruby and JavaScript are very similar to each other. Both are Object-Oriented Programming (OOP) Langauges, and both were built in the 1990s. There were, of course, several differences as well. JavaScript is a scripting language that was developed by Netscape to compete with C++ and ride on Java's popularity, while Ruby is  built by a computer scientist who wanted a "true" Object-Oriented experience. But the most surprising difference of all is the number of "objects".

In Ruby, everything is an Object. Strings are objects, arrays are objects, booleans are objects, classes are objects...if it exists, it's an object. If it doesn't exist, it's also an object: the object nil, part of the NilClass! The fact that everything is an object means that you can treat everything as an object, telling it to hold data and calling on its behavior/methods. You can define its methods simply by accessing the class the Object belongs to.

JavaScript behaves like most OOP languages though by not having everything be an object. Instead, JavaScript's objects behave very similar to Ruby's Hashes. While Ruby's Hashes refer to having 'values' stored in 'keys', JavaScript talks about 'values' being stored in 'properties' instead. To create a method, you simply store a function in a property. There are many, many other examples of non-Objects that exist in JavaScript, and they behave in other ways. 

Rubyists would prefer having everything be an Object because they can then add,remove and change methods, at will, for anything! This allows them to really customize the programming language to match their needs. JavaScript does not have the flexiblity that Ruby have, since not everything is an Object. This is not a bad thing though, as a programmer may not need to customize the JavaScript language and may be fine with its current system. It's also dangerous to be modifying the langauge if you do not know what you are doing, so, in a sense, JavaScript can be safer than Ruby.