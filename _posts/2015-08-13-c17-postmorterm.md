---
title_bar: Culture - Postmorterm for a Devbootcamp Project
post_title: Postmorterm for a Devbootcamp Project
post_subtitle: The Origins of "Hashography"
layout: default
---
Devbootcamp does not have a conventional 'final exam' like most schools. Instead, to graduate from the program, you must work with a team of like-minded individuals to build a full-blown website within 7 days. This was my experience in trying to build <a href="http://hashography.herokuapp.com/">Hashography</a>, a website that would display tweets about a certain word onto a Google Map.

Our project lead, Evangeline Garreau, was inspired by a news article about a professor who was able to trace the usage of certain words on Twitter and develop a heat map displaying his results. Evangeline found the system cool and wanted to replicate that with a website that would display the history of word usage throughout the entire world.

At first, the whole team was excited about the project. We wanted to determine the history of a word and be able to trace it from the very beginning. We also wanted to know where the words were being used, not just in the US, but globally. We had big dreams and aspirations for how to interpret the data and display it on a "heat map". All we had to do is just to grab those Tweets from Twitter.

But then those big ideas faced "technical limitations", which would be a euphemism for "cold hard reality". The best way to grab data from Twitter is to use an API. An API is a tool that enables websites (like Twitter) to communicate with other programs and websites (like "Hashography"). Twitter has two such APIs: a "REST API" that allows us to access past tweets, and a "Streaming API" that allows us to view present 'real-time' tweets.

It turns out that they were inherent limits to the Twitter REST API...such as the fact that Twitter would only allow us access to the last 7-10 days of Tweets. It also turns out that the professor that inspired Evangeline likely used the "Streaming API" for an entire year in order to grab the tweets necessary for him to discover the history. This option was incredibly impractical for our week-long project.

Our passion for the project turned into panic. We tried searching for alternative ways of meeting our project. We looked at Google Trends, which gave us all the data we need to trace the history of the word usage...except that if we end up using it, we would be pretty much copy Google Trends. We tried switching to a multimiedia approach that would use Instagram's photographs to present a history of the word, except Instagram's own API gave us trouble too. At some point, some members of our team even half-jokingly supported violating Twitter's Terms of Service agreement by building robots that would "scrape" tweets.

We floundered horribly.

By Friday afternoon, it was agreed that we had to pivot away from the original idea behind the project. The group overall came to an agreement that it was more important to see where tweets are located rather than see the "history" of the word (after all, Google Trends already gave us a good history of the word). We decided to use the Twitter Streaming API to grab current tweets of a word and then display them onto a map. We also decided that we never really liked seeing "heat maps", and switched to displaying data as points on a Google Map.

At the time, it seemed that we had "lost time", as we spent two days without any "progress". But we have learned a lot more about our tools and our limitations, enabling us to catch up quickly. We also were more willing to try everything possible to resolve any disaster that would confront us, including preparing backup plans in case our current "course-of-action" was not working. We ended up producing a workable website by Sunday, and started polishing and improving on it.

True, we still had problems after Sunday. We did not have enough automated tests and had to waste valuable time manually testing changes. We needed to learn the "best practices" for the new tools we were using. We needed to refactor our code constantly. We had trouble with designing our website to be user-friendly. But those were problems that we could **fix** as part of standard maintenance, and they were much easier problems than trying to build the website in the first place. The very act of having a physical web presence gave the team a big morale boost.

User feedback was excellent, and people saw our program as being 'beautiful and meaningful'. Our "pivot" was a success.

Why was it a success? For me, I think it was just due to the fact that we <s>panicked</s> realized the extent of our situation early, and thus was more willing to do "whatever it takes" to accomplish our goals, including changing our goals to something more feasible. Our project lead, Evangeline Garreau, would instead likely credit the fact that we had good group dynamics and that we respected each other's ideas. (Of course, both thoughts may be true.) And, of course, we may have just been lucky.

Overall, we did a good job with this website, and it showed us ultimately that we can still produce beautiful and meaningful work without necessarily staying true to the original idea. We were humbled by the experience, and only by being humble can we begin to learn from our surroundings. We had fun, and we learned a lot.