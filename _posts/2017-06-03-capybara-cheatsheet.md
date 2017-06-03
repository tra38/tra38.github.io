---
title_bar: Technical - Capybara
post_title: Please Read the Documentation Beforehand
post_subtitle: A Case Study In Making Foolishing Assumptions When Interacting With Forms Using Capybara
layout: default
---
Capybara is a very useful tool for writing integration tests, but it can be very hard to get used to its DSL for interacting with forms. It is even worse when you don't read the documentation for using the DSL, and instead only trust the source code of existing integration tests.

First, here's a small cheat sheet for form interaction (for my personal use).

```ruby
# Text Field or Text Area
fill_in 'Text Field', with: 'Lorem Ipsum'

# Select Field
select 'Lorem Ipsum', from: 'Select Field'
unselect 'Lorem Ipsum', from: 'Select Field'

# Checkbox
check 'Lorem Ipsum'
uncheck 'Lorem Ipsum'

# Radio Button
choose('Lorem Ipsum')

# File Upload
attach_file('File Upload', '/path/to/image.jpg')
```

Of course, while writing out this cheatsheet, I realized that it already  existed in the [main Capybara README documentation](https://github.com/teamcapybara/capybara#interacting-with-forms). I missed it though because I...er...didn't read the documentation before I started using Capybara.

The reason I didn't read the documentation was that I thought it wasn't really necessary. After all, I saw how other people used Capybara in the real world. And after seeing how other people wrote Capybara integration tests, I thought that *all* ways of filling data into forms required using fill_in...

```ruby
#My imaginary understanding of the DSL

fill_in 'Text Field', with: 'Lorem Ipsum'
fill_in 'Select Field', with: 'Lorem Ipsum'
fill_in 'Checkbox', with: 'Lorem Ipsum'
fill_in 'Radio Button', with 'Lorem Ipsum'

# okay, I didn't quite know how I would imagine file upload to work...
# I assumed at least some variant of fill_in
```

I guess I imagined that there was a lot of magic involved with fill_in, and all I have to do is to specify the proper text label and Capybara will handle the rest. That was of course wrong...and I realized I was wrong ~4 hours after trying to coerce "fill_in" to handle a Select Field. (To make matters worse, I slowly began to realize my assumptions were wrong after reading the only realized I was wrong after reading the API documentation for two hours.)

The reason that I thought that "fill_in" was this magic, all-purpose method was that all the integration tests that I read that used Capybara interacted with forms that only had text fields. Their code worked perfectly, so I just made a simple assumption that the logic would transfer over elsewhere to other form fields. That assumption was wrong.

So I learned two lessons:
(A) Even when you're learning how an API works from working code, it may still be useful to look at the documentation anyway. Working code may be  dependent on certain quirks that has very little to do with the language itself...and you may not be aware what those quirks are, except in retrospect.
(B) When you're reading the documentation, make sure to look at the README first and then, if the README doesn't help, only **then** look at the API Documentation. While both forms of documentation would eventually teach me the correct DSL syntax, the README documentation is much more accessible (probably because more people are going to see it) while the API Documentation can be very technical and can miss sight of the bigger picture. To truly understand the API Documentation, you need to first understand the README documentation.