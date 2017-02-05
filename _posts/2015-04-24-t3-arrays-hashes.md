---
title_bar: Technical - Arrays versus Hashes
post_title: Arrays versus Hashes
post_subtitle: The Difference
layout: default
---
An **array** is a list of items, like a shopping list. An example array would be:

<code>["milk","bread","eggs"]</code>

The array also keeps track of the order of said items, so it knows the first item is "milk", the second item is "bread", and the third item is "eggs". However, programming languages counts from zero, not from one. So you would have to look for the 0th item to get "milk", the 1st item to get "bread", and the 2nd item to get "eggs".

A "key-value pair" is an item (called a "key") with another item (called a "value") attached to the "key". Most programming languages also have a certain type of 'object' that can store these "key-value pairs", but they call this 'object' different names. Ruby call this 'object' a **Hash**. A Hash is like a dictionary. An example Hash would be:

<code>{ "milk" => "white liquid", "bread" => "food made out of flour", "eggs" => "round objects"}</code>

The "word" ("milk") is the key, and the definition ("white liquid") is the value. Just like arrays, Hashes also keep track of the order, so you could look for the 0th item to get "milk", and its value. But it's not necessary, because you can always look up the key itself, and find the value in the Hash.

Hashes and arrays both have their uses. If you just want a list of items and do not want to attach data to those items, then you would use an array. If, however, you do want some data associated with each item on your list, you would use an Hash.