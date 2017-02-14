---
title_bar: Technical - Resumé Driven Development
post_title: Expert Resumé Driven Development
post_subtitle: The Passionate, Functional, Micro-Serviced Approach To The Job Hunt
layout: default
---
Disclaimer: I wrote the book ["Essential Copying and Pasting From Stack Overflow"](https://tra38.gitbooks.io/essential-copying-and-pasting-from-stack-overflow/content/), which was inspired by a cover designed by [ThePracticalDev](https://twitter.com/thepracticaldev?lang=en). This blog post is also inspired by a cover designed by ThePracticalDev. Just like "Essential Copying and Pasting From Stack Overflow", "Expert Resumé Driven Development" is also written in a deadpan manner.

<img style="float: left; height: 30%; width: 30%" src="http://i.imgur.com/DQcks8u.jpg" alt="Cover for Resumé Driven Development, 'The Passionate, Functional, Micro-Serviced Approach">

<h3>What is "Resumé Driven Development"?</h3>

Resumé Driven Development refers to the practice of choosing hot new technologies for your projects to make your resumé more impressive. For example, you want to write a program in that hot new Javascript micro-generator framework ["Plop.js"](https://github.com/amwmedia/plop)...because it's a hot new JavaScript framework. Sure, you can use the technologies that you already know and are probably better suited for the job, but that wouldn't be as impressive as riding the hot bandwagon. You don't even know what "Plop.js" is, but you'll find out soon enough.

There is some controversy on whether Resumé Driven Development is actually good. [Paul E. Davis defended the practice](http://willcode4beer.com/opinion.jsp?set=in_favor_of_rdd) as it is an indictator that the developer is willing to learn new technologes instead of sticking with potentially obsolete solutions. Sure, "Plop.js" may not actually be suited for your use case, but at least you showed that you *can* learn it and use it quickly, and that you could later on find the bleeding-edge technology that might actually be useful.

"In the end, if developers are not concerned with their own careers, it's not likely they'll be concered with your business."---Paul E. Davis

Most developers seem to detest RDD though (as can be seen by [this parody website](http://rdd.io)). There is a general belief that developers are not using using the hot new technologies in their spare time, but instead [using them on company projects](http://www.healthcareguy.com/2007/01/19/resume-driven-development-rdd/). This is a colossal waste of company funds, as the technology may be ill-suited for the task at hand and can lead to long-term maintanance headaches.

Developers are not the only people that engage in Resumé Driven Development. Management may also engage in RDD [during the hiring process as well](http://radar.oreilly.com/2014/10/resume-driven-development.html). If a job vacancy exists, there is a desire to hire a new programmer with the same skillset of the old programmer. So the old programmer was an expert in Plop.js, then the job posting will read "6 months  experience with Plop.js". This may be a very bad thing because you are optimizing for knowledge of certain technologies, instead of choosing the "right tool" for the job. If you only hire Plop.js developers, you will only get Plop.js websites.

RDD is probably a subset of a larger [Principal-Agent Problem](https://en.wikipedia.org/wiki/Principal–agent_problem). The Principal (management) hires an Agent (a developer) to build a program and allow the Agent to choose the tech stack. But the Agent's interest (making his resumé more impressive) can be orthogonal to the Principal's interest (producing a great product by using the "right tool" for the job). If the Principal allows the Agent to do as he wish, then the Agent **will** do as he wishes, thereby leading to the Agent to prosper and the Principal to suffer.

RDD is composed of two sections: the Resumé and the Technology. Let's look at them both briefly.

<h3>The Role of the "Resumé"</h3>
A resumé serves to let people know what you have done, in the hopes of getting people impressed. According to [a study by TheLadders, a resume re-writing company](http://cdn.theladders.net/static/images/basicSite/pdfs/TheLadders-EyeTracking-StudyC2.pdf), recruiters can spend 6 seconds per  resumé, scanning for keywords and cursory background information about your education and job history before deciding whether you are "fit" or "no-fit". You can see why some developers want to maximize those 6 seconds by practicing RDD.

Now, there is not that much in-depth examination of what's on the resumé. If someone says that they used Plop.js when building a Uber-For-Dogs application, then you assume that they did use Plop.js and that there actually is a Uber-For-Dogs application...that he really spent 6 months on it...and that he got to pet a unicorn while on the job. It says so on the resumé. Just keep scanning for more keywords then.

You can see where I'm going here. Resumés can lie. You can claim to have worked on sixty Plop.js projects in closed-source companies, and provide fake phone numbers and references as 'proof' that these closed-source projects exist. Lying is horribly unethical, and I would not recommend it for anyone to do. But it can be done, and is probably more efficent than a pure RDD approach...at least in getting the foot in the door. However, at the interview stage, interviewers will attempt to weed out those that did lie on their resumés - such as asking basic questions like "What is Plop.js?".

So the better option is to actually use the technologies on real projects then, so that when you get to the interview stage, you can actually prove your expertise in it and not be exposed as a fraud. That (sadly) means you do have to build a Uber-For-Dogs application just so you can use the Plop.js keyword. You may even need to provide a link to the application and show the source code, in case someone looks at your resumé for longer than six seconds. However, once you do this, you do not have to worry about proving anything else. If you can demonstrate that you can use Plop.js, then most people will assume that you know how to use it.

<h3>Choosing the Hot Technology</h3>

The biggest problem with choosing hot new technologies isn't actually learning them. It's difficult, and you'll have to deal with bad documentation and difficult solutions, but given enough time and persistence, you will eventually succeed.

No, the biggest problem with choosing hot new technologies is that you don't **know** what is actually hot.

You can guess. You can listen to a community, and if the community talks a lot about Plop.js, then that suggest that Plop.js is hot. If the community stops talking about Plop.js, then Plop.js must not be hot. You can bookmark [Google Trends](https://www.google.com/trends/) and pay attention to what words people are searching. You can look at job postings and see what keywords the recruiters are using. And so on and so forth.

But they're all trailing indictators. It doesn't help you predict whether that tech will stay hot in the future.

It is here that Gartner Hype Cycle can be most useful for an RDDer. Gartner argues that all new technologies go through a cycle. I described the Hype Cycle in [my blog post against Artifical Intelligence](http://tra38.github.io/blog/ai3.html)...and I reprint my comments on this cycle here:

<img style="float: right;" src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/94/Gartner_Hype_Cycle.svg/559px-Gartner_Hype_Cycle.svg.png" >

>At first, people become very interested in a brand new technology (a "Technology Trigger"). Companies start to over-invest in researching this technology, leading to a "Peak of Inflated Expectations" (i.e, a bubble). But the technology turns out to have major limitations. As a result, investment in the technology dries up ("Trough of Disillusionment"). Most companies either begin laying people off or closing down outright.

>Eventually, the survivors soon realize how to use the technology properly ("Slope of Enlightenment"), and we can finally use the technology in our day-to-day life ("Plateau of Productivity"). But as this picture from Wikipedia shows, the visibility of the technology in the Plateau of Productivity is much less than the visibility of that same technology in the Peak of Inflated Expectations. The brand new technology has done great things for us. It's just not as great as we hoped it to be. And does it justify the extreme waste seen in the "Peak of Inflated Expectations"?

Since the technology reaches the maximum visibility/hype in the Peak of Inflated Expectations, this implies that, by the time you hear of a tech, *it's already too late*. The only people who would be able to take advantage of the hype are the 'early adopters', and they are the ones who will likely reap most of the benefits (though they also accept most of the costs as well, since not all new technologies are interesting or useful enough to go through this Hype Cycle).

Another message this charts tells us is that the best time to learn a new technology is either during the Technology Trigger or the Trough of Disillusionment.

During the Technology Trigger stage, there are no experts. There are only a few people who know your keyword. Specializing now as an 'early adopter' (while the field is still young) would be much more impressive than being an expert during the Peak of Expectation, when you have thousands of 'experts' in your field. Building a bot that can draw paintings now seems neat. Building a paint-bot five years from now, when every programmer have already built their own personal paint-bot? **Boring.**

During the Trough of Disillusionment, you are able to take advantage of previous research done during the Technology Trigger and the Peak of Inflated Expectations, learning from past successes and failures with the tech. You also will have less competition during the Trough, as most programmers have already left to move onto the next "hot" technology. Eventually, interest in the tech will revive, and your lovely keyword will regain some allure.

Any other time to study a technology would carry either too much competition (the Peak of Inflated Expectations) or too little reward (the Plateau of Productivity) to justify the expense. The only reason you would want to study the technology in that case is because you think it might actually help you grow as a developer.

<!-- Now, if you are not dealing with recruiters but instead cold-calling or networking with companies directly, then it is possible that a company will probably do more in-depth research on you before deciding "fit"/"no-fit". This may seem good (more than 6 seconds' attention) but it also means that your resumé itself might play a lesser role in the deciding process (lessening the need for RDD). Instead, your Side Projects and GitHub Open Source contributions might play a larger role (though you can also highlight that on your resumé). -->