---
title_bar: Culture - Bot Traffic
post_title: Untold Problems of a Software Blog
post_subtitle: Bots
layout: default
---
[According to a 2015 report by Incapsula](https://www.incapsula.com/blog/bot-traffic-report-2015.html), 48.5% of all web traffic are by bots. If you are running a *small* website (10 to 1000 visits per day), 85.4% of your web traffic are by bots. Even if you happen to run a very large website (100,000 to 1 million visits per day), 39.7% of your web traffic are by bots.

Put it frankly, most of your audience are composed of robots. (I've learned this the hard way when I was maintaining a website for a Texan religious organization and found out from Google Analytics that 90% of people visiting the site were from Russia.)

A minority of bots are "good bots" - crawlers and web scanner tools. Their goal is to visit websites and provide valuable information to another user. Search engines  aggregating results based on keywords, chatbots looking to answer users' natural language queries, etc. [Googlebot](https://support.google.com/webmasters/answer/182072?hl=en) is a prime example of a "good bot" (and is actually pictured in the header of this blog post holding flowers).

The majority of bots are "bad bots" - scrapers that are harvesting emails and looking for content to steal, DDoS bots, hacking tools that are scanning websites for security vulnerabilities, spammers trying to sell the latest diet pill, ad bots that are clicking on your advertisements, etc. (Okay, the ad bots are probably "good" from the perspective of the blogger with ads, but they're still pretty bad for [the companies paying for the ads](http://www.adweek.com/news/advertising-branding/whats-being-done-rein-7-billion-ad-fraud-169743).)

I have delivered a speech about bots in June 2016 - [here's the slides for it](https://docs.google.com/presentation/d/1gK6KmL_dtwk_8477Jc6GeLAipZMLoMVxFa9TIffggcQ/edit#slide=id.g142d681b2f_0_187). But I am writing this blog post as a response to [Untold Benefits of a Software Blog](https://dev.to/liquidise/untold-benefits-of-a-software-blog). The arguments in that blog post are correct. But any discussion of blogging must take into account the audience of that blog. And that audience for most websites will be machines. Here's the problems that bots can cause:

**Your Metrics Are Unreliable** - You can hire a botnet to visit your website, scroll up and down the page, execute JavaScript to trigger your analytics software, click on ads and other links, write comments about your blog post, like your blog posts, retweet your blog posts, etc., etc. Even if you don't want to fake your metrics to boost your vanity, bots may still behave as normal users to avoid detection by other algorithms. This may mean that they will visit multiple "innocent" sites (including yours) before heading over to their final destination. Bad analytics make it difficult to target your content properly, since how else would you know if your content is actually working on human beings?

**You Are Writing For the Machine** - There is just so much content on the Internet that humans are unable to consume it all. So they rely on aggregators and filters. But content producers then realize that they shouldn't write high-quality content. That is useless because nobody will discover high-quality content without the help of aggregators and filters. Instead, content producers should write content that appeals to aggregators and filters. This is the ultimate premise behind SEO (search engine optimization), and the end conclusion is people writing articles with long-tail keywords to secure visits from search engines. SEO is the natural consequence of [Goodhart's Law](https://en.wikipedia.org/wiki/Goodhart's_law) ("When a measure becomes a target, it ceases to be a good measure"). Search engines' dependence on links to determine whether websites are popular or not led to the rise of ["link farms"](https://en.wikipedia.org/wiki/Link_farm#History). Google was also responsible for the rise and fall of [content farms](https://en.wikipedia.org/wiki/Content_farm) such as [eHow](https://en.wikipedia.org/wiki/EHow) - Google's algorithms once prized such "fresh content", only to later changed their minds with [the "Panda" updates](https://en.wikipedia.org/wiki/Google_Panda). Even today, Google [encourages "quantity over quality" in content generation](http://relevance.com/how-google-ruined-content-marketing/):

>While one high-quality article might drive a thousand shares, 10 articles that drive 120 shares each is more. Replace shares with traffic or conversions. It’s the same concept. In this way, Google is actually encouraging us to commoditize our content in lieu of creating great content, whether it’s purposeful or not.

[This perverse trend is ultimately unsustainable](https://dev.to/tra/nanogenmo-2016-and-my-predictions-about-text-generation/comments/3i), but it may still continue for a while longer. Marketers are already discussing [how the Washington Post is able to quickly generate more content by using algorithms](http://buzzsumo.com/blog/future-lot-content/), and how incumbents could drown out  competition from upstarts [by mass-producing low-quality content](https://www.businessesgrow.com/2016/09/19/crappy-content/).

**Your Content Will Be Divorced From You** - Content on websites such as dev.to are reposted elsewhere, word-for-word, by scrapers programmed by Black Hat SEO specialists. These specialists hope to populate their websites with cheap content...and what could be more cheap than copying and pasting? If you're lucky, they're willing to give you a backlink as a meaningless "thank-you note" for providing the content that they so desperately need. Most of the time, they won't bother. Even "legitimate" actors such as Google are getting into the business of taking your content and reusing it, through the use of [featured snippets](https://support.google.com/webmasters/answer/6229325?hl=en).

However, a new breed of scrapers exist - intelligent scrapers. They can search websites for sentences containing certain keywords, and then rewrite those sentences using "article spinning" techniques. As much as I find it distasteful to link to Black SEO sites, here is [a YouTube demonstration for Kontent Machine 3](https://www.youtube.com/watch?v=sV8KvC420SM&t=13s), one of these intelligent scrapers (so you can observe how it works). The output is decent enough to please a search engine algorithm, but still need work before humans could also enjoy the output. (Disclaimer: I am working on 'content aggregation' software that can take paragraphs from an external CSV file and then rearrange them into unique articles. I am still thinking of a good way to open-source it without helping intelligent scrapers.)

I think it is likely that as text generation techniques get better and as AI becomes more advanced, people will begin recycling content...downplaying or even eliminating the content creator from the picture. The machine curator is praised while the human content creator is devalued or ignored.

I gave a more positive spin of this trend in the article [Who are the Audiences of Computer-Generated Novels?](https://dev.to/tra/who-are-the-audiences-of-computer-generated-novels), in the section entitled "People Who Want To Consume A Existing Corpus". After all, there's just so much data out there that we do need algorithms to make sense of it all, and the curator does deserve some "credit" for its role in bringing order from chaos. And these algorithms are exciting. But exciting algorithms also carry negative consequences as well -- consequence that we have to be aware of and prepare for.

Imagine a chatbot that resides in your terminal. You can ask this chatbot a coding question, without ever going to StackOverflow and seeing a person's name or (shudder) avatar:

<pre>
#> howdoi python for loop
#=>
#for idx, val in enumerate(ints):
#    print(idx, val)
</pre>

That world already exist. It's called [howdoi](https://github.com/gleitz/howdoi), a open-source command-line tool. Of course, it's not perfect (neither is StackOverflow), but what surprised me the most about howdoi is that it can do qualitative answers as well:

<pre>
#>howdoi evolutionary algorithm
#>The pro: Evolutionary algorithms (EAs), as genetic algorithms (GAs), are general
# purpose optimization algorithms that can be applied to any problem for which you
# can define a fitness function. They have been applied to nearly all conceivable
# optimization problems, see e.g. the conference series on „Parallel Problem
# Solving from Nature“. The con: EAs are generally much slower than any specific
# optimization algorithm adapted to the problem. I would apply them only if all
# standard optimization algorithms fail.
</pre>

<pre>
#>howdoi solve the halting problem
#>The normal approach is to constrain program behavior to an effectively calculable
#> algorithm.  For example, the simply typed lambda calculus can be used to
#> determine that an algorithm always halts.  This means that the simply typed
#> lambda calculus is not Turing complete, but it is still powerful enough to
#> represent many interesting algorithms.
</pre>

Humans wrote this content. But humans are being denied credit for their effort, as it is the algorithm ("howdoi") that is curating this content and showing it to the end user. Note the lack of backlinks in the outputs of "howdoi" as well, meaning "howdoi" is technically engaging in plagiarism. "howdoi" is the future, and the future doesn't look good for human content generators.

**Conclusion**: I am not *necessarily* saying "Don't bother writing blog posts because the only people who are going to read them are bots". There are good reasons to write a blog post. Just know that humans are not your primary audience for these posts. If you treat blogs mostly as vehicles of self-expression and communication with other people within a niche, then you'll go far. If you treat blogs as a ticket to gaining fame with other human beings though, you're probably going to fail hard.

**Correction**:
 - While it is true that howdoi is currently engaging in plagiarism, [the developers are aware of this](https://github.com/gleitz/howdoi/issues/152) and [a PR have been opened up to fix this issue](https://github.com/gleitz/howdoi/pull/153).

 *Note* - This article was originally published on [dev.to](https://dev.to/tra/untold-problems-of-a-software-blog---bots) on Jan. 7th 2016, and has since ported over here.