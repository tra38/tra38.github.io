---
title_bar: Technical - Cutting-Edge Tech
post_title: The Difficulty of Writing About Cutting-Edge Technology
post_subtitle: Or, My Experience In Writing About Text Generation
layout: default
---
This month, I finished a blog post series about "text generation" -- or less jargony, programming computers how to write. This blog post series is available on the Practical Developer website (for mass consumption by a technical audience).

Here are the links to those blog posts, in order of publication:

- ["Structure" in Computer-Generated Novels](https://dev.to/tra/structure-in-computer-generated-novels)
- [Using Templates in Computer-Generated Works](https://dev.to/tra/using-templates-innbspcomputer-generated-works)
- [The "Commonsense" Problem in Computer-Generated Works](https://dev.to/tra/the-commonsense-knowledge-problem-in-computer-generated-works)
- [Who are the Audiences of Computer-Generated Novels?](https://dev.to/tra/who-are-the-audiences-of-computer-generated-novels)

I started this series due to [my recent experiments in text-generation](tra38.github.io/c23-one-year-later.html). I wanted to collect all the knowledge about that field so that other people wouldn't have to focus on reinventing the wheel.

For example, [Prolefeed](https://github.com/tra38/Prolefeed) is a Ruby gem that was based on an algorithm that I invented in 2015. You give the algorithm pre-made content, and then the algorithm randomly shuffles its order. This algorithm was so simple that I wondered whether it was already invented.

Well, it was. In 1986, Judy Malloy worked on [*Uncle Rogers*](http://www.well.com/user/jmalloy/uncleroger/uncle.html), an art project that also doubled as a computer program. One file in this project is called ["Terminals"](http://www.well.com/user/jmalloy/uncleroger/188.html) - the program would randomly select paragraphs from a "corpus" and then display them to the user[1]. Paragraph shuffling was [also independently discovered and used in 2011](http://www.warriorforum.com/main-internet-marketing-discussion-forum/322057-their-tool-shuffles-paragraph-order.html) to create spam articles that would trick Google into indexing their site and ranking them high in search rankings (an example of "Black Hate SEO").

There are probably other examples where random shuffling was [independently discovered](https://en.wikipedia.org/wiki/Multiple_discovery). The point is to stop this sort of "multiple discovery" from ever happening again. Text generation itself had a long history of academic research [starting in the 1970s](http://wikis.sub.uni-hamburg.de/lhn/index.php/Story_Generator_Algorithms), and yet there has been a cycle where this technology is discovered, forgotten, rediscovered, reforgotten, etc., etc.

It seemed more reasonable to document this technology so that users don't have to worry about writing brand new code that somebody already written 10 years ago. They could instead read these articles and learn from them, and then build off that knowledge to produce something brand new and innovative.

However, by I started work on Article #4 in my series, I realized a flaw in my thinking. In my attempts to write about text generation, I realized that I was attempting to catalog the field...with all its nuances and quirks. Every attempt to add a new category only serves to reveal the flaws of my previous categorizations.

For example, in Article #3, I wrote about the possibility of people treating computer-generated works as its own genre...with its own unique fanbase. While planning Article #4 though, I realized that there are *two* unique fanbases for computer-generated works. The first fanbase loves computer-generated works for being a form of "conceptual art", and the second fanbase likes the idea of consuming repetitive content. If there are two fanbases, are there *two* different genres then? The clear idea I had in Article #3 was  undermined by details in Article #4.

The Argentine writer Jorge Luis Borges wrote about my dilemma in the short story [The Analytical Language of John Wilkins](http://www.alamut.com/subj/artiface/language/johnWilkins.html). John Wilkins wanted to create a language that would seek to explain the universe. But the problem with such a language is that the language's very construction would be arbitrary and based on cultural biases. There will always be "ambiguities, redundancies and deficiencies" in any attempt to categorize the universe, and such attempts at categorizations reveal more about the author than about the universe itself.

Text generation is a field that is smaller than this universe. But it is still an extremely broad field, with its own hidden depth. Any attempt to fully cover the field would fail, and deciding what topics to cover and what topics to ignore is a very difficult (and rather arbitrary) choice. Rather than following in John Wilkins' attempts to build the universal language, it would be better to simply end the blog series on a high-note.

This is why writing about "cutting-edge technologies" such as text generation is so difficult. There is no way for a single human to fully explain the field coherently and objectively, no matter how many words he or she writes. What is left is a rather incomplete and biased picture of the world, not truly comprehensive or representative of the broader field. To truly understand the field and to avoid reinventing the wheel, you will likely have to do your own research into the field, learning from the biased viewpoints of others and trying to synthesize them together to create your own biased viewpoint.

We are all [blind men feebly trying to understand the elephant](https://en.wikipedia.org/wiki/Blind_men_and_an_elephant).

[1]The "Terminals" web app simulates randomly picking paragraphs from a corpus by having a blank keyboard that a user can click on, but if you are interested in a demonstration with no user interaction...please look at [Another Party In Woodside](http://www.well.com/user/jmalloy/uncleroger/Another_Party_in_Woodside.html) (a more recent program written by Judy Malloy).