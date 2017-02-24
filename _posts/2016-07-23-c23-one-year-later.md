---
title_bar: Culture - The Ozymandias Gambit
post_title: The Ozymandias Gambit
post_subtitle: Over A Year
layout: default
---
>Most people think spies are afraid of guns, or KGB guards, or barbed wire, but in point of fact the most dangerous thing they face is paper. Papers carry secrets. Papers can carry death warrants. Papers like this one, this folio with its blurry eighteen year old faked missile photographs and estimates of time/survivor curves and pervasive psychosis ratios, can give you nightmares, dragging you awake screaming in the middle of the night.---[A Colder War](http://www.infinityplus.co.uk/stories/colderwar.htm)

Humans have written papers all their lives. Writing was once considered a praiseworthy activity that required intelligence.  But technology has now advanced to the point that computers are able to imitate the very process of writing successfully, and we are forced to decide between two unappeasing statements:

 - Computers must be intelligent.
 - Writing doesn't require intelligence.

This is, to me, pretty scary for a variety of reasons: loss of purpose and ego issues, possible rise in unemployment, human dependency on technology to do all the work for them, etc. And I wanted to do something to counter the rising power of AI.

[EDIT, Feb. 23rd 2017 - This statement may seem rather "Luddite" if divorced from context, so I am adding this edit note as clarification of my intent. I am not specifically opposed to AI as a technology in and of itself, because AI is useful and have its benefits. But AI also have risks as well, and what I noticed is the lack of societial regulations meant to deal with those risks.

I don't think this is controverisal, per se, to suggest that society needs to take steps to contain the very real dangers of AI, maximizing its benefits while minimizing its damages. Progress is not always positive, and the dangers of AI can outweigh its benefits...if progress is not carefully controlled.]

It has been 15 months since I first entered DBC, almost one year since I graduated from Dev Bootcamp. During that time, I attempted to research the emerging field of computer-generated literature...in the hopes of using this technology against them, as a form of advocacy against uncontrolled research into AI.

During the on-site portion of the DBC curriculum in Chicago, many people learned about this plan, especially after I produced [Friend Computer](https://github.com/tra38/FriendComputer), a blog written by a computer, as a standalone DBC project. However, since then, I have not been in much contact with the people on DBC ever since my graduation...and so I decide to write a blog post to explain what happened.

I'll start by quoting an email that I sent to a random stranger:

>Let me introduce myself fairly carefully. I like to write. When I was a teenager, I served as a volunteer journalist. In college, I published a research paper. Even today, I write nonfictional blog posts and some (unpublished) fictional stories. So I still write, although I do not identify myself as a "writer". My day-job is a computer programmer...where I write computer code (although it may not be beautiful or elegant to read).

>I had very some uncomfortable feelings about artificial intelligence and technology...especially our overt dependence on it and its potential impact on humanity. After reading an article about Narrative Science and its robojournalist articles, I wanted to take a stand against technological progress causing us to "shoot ourselves in the foot" [by writing a dystopian novel about an AI supercomputer that ruled over human society with an iron fist].

>And I immediately realized that this novel had to be computer-generated. It had to be that way. If I "handwrote" a sci-fi novel about the dangers of technology, then it would just be my opinions, my thoughts. Not reality. Nobody would listen to the thoughts of a random person, and would simply dismiss my fear as "Luddism". If I am able to build proof of the dangers of technology (computer-generated literature), then that would make my arguments against technology more persuasive. "If technology can do X now, what about the future?" Etc., etc.

The "Ozymandias Gambit" is the term that Duke Greene (a DBC teacher) named my scheme. It is named after the character from the "Watchmen" comic book series. Ozymandias, the main villian of the comic book series, wanted to end the Cold War by creating a Lovecraftian monster to attack both the United States and the Soviet Union. His hope is that this monster would scare the superpowers long enough to unify together, thereby forestalling the possibility of nuclear armageddon.

I built ["Skynet"](https://github.com/tra38/Skynet), a command-line program that can be used to generate stories based on a "Mad-Lib"-style template. Someone even built [a Python script](https://github.com/enkiv2/Skynet/blob/master/txt2sky.py) that can turn existing novels *into* templates that can then be used to generate stories...and used it and [a configuration file](https://github.com/enkiv2/Skynet/blob/master/odyssey.dict) to generate a Sky template of [The Odyssey](https://github.com/enkiv2/Skynet/blob/master/odyssey.sky).

Now, certainly, I could have actually produced the anti-technological novel with this tool I had. But I would have to *write* out all the templates in question, which almost defeats the whole purpose of building the program. The templates would have done most of the work, while the computer in question really only randomly select words to plug into the templates. So I gave up on that line...and tried other approaches to procedural generation.

As for expressing my ire about technology, I did find other outlets. I wrote algorithms to generate [two short stories against technology](https://medium.com/laughter-in-the-singularity) and [a blog post condemning artificial intelligence](tra38.github.io/blog/ai3.html). There was still some human involvement involved. I wrote all the words in the short stories and the blog posts. But the algorithm also played a role in deciding the order of my paragraphs within the story. And the order matters just as much as the text. I even released my algorithm as an open-source Ruby gem called [Prolefeed](https://github.com/tra38/Prolefeed).

So, yeah, I carried out a lesser version of the "Ozymandias Gambit".

*Most people didn't care.* Those that did can be placed into two camps, the Futurists and the Traditionalists:

##The Futurists
There are those who really liked the technology that I was working on. They saw it as cool and exciting, and thought about improving on my methods. Which, of course, *misses the point.*

Which is why I started my blog post by quoting from "A Colder War" instead of from the "Watchmen". "A Colder War" is a novella that had a premise: What if the superpowers discovered Lovecraftian technologies? The answer was simple...they started using it to fight their Cold War! The 'paper' that the quote was referring to is a CIA report about Soviet Union's "Project Koschei" (a plan to use Cthulhu as a superweapon against the United States).

So Ozymandias may have been too optimistic. Instead of seeing Ozymandias' monster as a wakeup call, the superpowers could have simply started building their own monsters instead. I mean, Ozy already did it. How hard could it be?

Ozymandias could, of course, take a perverse pride in contributing to the very fear that he opposed. In fact, he'd probably make a killing selling his monster-building techniques to the superpowers. But the irony is there. It cannot be concealed or denied.

##The Traditionalists
These people did view technology as a threat, and thus would sympathize with my anti-tech rants. They were mostly creeped out by the possibility of text generation. The computer-generated text may not be 'on par' with human-generated work, but it could improve with time..and besides, computer-generated work doesn't have to be "good". It just have to be "good enough". This audience was receptive to my message.

But that's it. Having felt chills down their spine, they haven't moved a single inch to stop this trend. It's almost as if they couldn't *do anything* to stop it. There is almost a sense of resignation...that you can't fight progress. I guess the best you can do is write against the future...but then again, I already wrote an algorithm to write against the future.

In this scenario, people saw Ozymandias' evil monster, but resigned themselves to the fact that it existed and moved on with their lives. "Yeah, a monster destroyed New York. What a shame. So whose going to win the Super Bowl this year?" It's not like they hate the future...they certainly do. But they realize that they can't change it. All they can do is to accept it and prepare for it.

##The Failure of the Ozymandias Gambit
Today, I sometimes "write" computer-generated blog posts about computer-generated literature and [post them on dev.to](https://dev.to/tra), with plans to eventually port them over to this site. I like to inform people about this field and its technical merits, while also conveying my distaste and disgust at the field as well.

[EDIT, Feb. 23rd 2017 - This distaste and disgust is not based on the technology itself, as the technology is very cool and exciting. However, there are uncontroleld risks with AI. That's what I express my distate and disgust at -- that there's problems with AI as well and we humans don't have a good solution to deal with these problems.]

This blog post, however, was not computer-generated. I could have wrote an algorithm to write this blog post. I have to break this blog post up into smaller chunks, and then use [Prolefeed](https://github.com/tra38/Prolefeed) to shuffle the chunks. It is fairly easy (although time-consuming) to pull off. But today, I just wanted to express *my* own feelings about my experience. Not what the computer wanted to write about. Maybe the computer might be a better writer than me. But I still want to vent my thoughts anyway. (Duke Greene, my DBC teacher, have also said the same thing about his own creative works...he likes doing them manually because he wants to express his own thoughts, without any such mechanical filters.)

I'll probably keep writing against the future, warning people about the possible disaster of artificial intelligence and how we need societal regulation against it to limit its damages. But now I am under no illusion that my posts will actually change anything. At least I tried.