---
title_bar: Technical - Inline, Block, and Inline-Block
post_title: Inline, Block, and Inline-Block
post_subtitle: The difference is in the display...
layout: default
---
Ever wonder how web developers are able to put images into horizontal rows, creating neat "galleries"? This blog post explains how web developers are able to create these galleries.

**What is HTML and CSS?**

Just like there are hundreds of  "languages for humans", there are also hundreds of "languages for computers". HTML is one of those "languages for computers", and its goal is to help your web browser understand how to display a website.

But today HTML is used to only create a website, not to make it look beautiful and interesting. Instead, we have a second "language for computer" to help your web browser  make websites beautiful. That language is called Cascading Style Sheets (CSS). Good web developers must be masters of both HTML and CSS.

One thing that CSS affects is how images and text are displayed on a website. This is done through modifying the "Display" property in CSS. There are several different types of ways to modify "Display", but the three most famous 'display' variables are Display: Inline, Display: Block and Display: Inline-Block.

**Display: Inline**

<img src="../img/inline.png" class= "horizon" />

Inline ensures that text and images stays in nice, neat horizontal rows. For text, inline is a great property to have, because then you can read the text easily. But this picture has colored recentagles, which were given a certain width and height. To ensure that the recentagles are in nice, neat rows, "inline" ignores the dimensions of the recentagles and resizes them. If we want to make sure the rectangles keeps the same dimensions that we give it, we must use...

**Display: Block**

<img src="../img/block.png" class= "horizon" />

Block places each image on their own seperate row. There is also some whitespace to seperate the image from anything else on the website. This is good for putting images vertically on top of each other. The recentagles also keeps the width and height that we assigned it. But 'display: block' prevents us from putting images into horizontal rows. What if...we can combine both?

**Display: Inline-Block**
<img src="../img/inline-block.png" class= "horizon" />

Inline-Block is a combination of both Inline and Block. The recetangles are placed on a single line, but keep their original dimensions. So instead of images being placed vertically on top of each other, now they are horizontally next to each other!

There are many uses for these three display properties. But because galleries require vertical rows and and images to keep their original size, most web developers use "Display: Inline-Block" when making web galleries.