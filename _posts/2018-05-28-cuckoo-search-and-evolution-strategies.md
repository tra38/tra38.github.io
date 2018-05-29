---
title_bar: Technical - Cuckoo Search and Evolution Strategies
post_title: Comparing the Pseudocodes of Cuckoo Search and Evolution Strategies
post_subtitle: My First Foray into Understanding Metaheuristics
layout: default
---
EDITOR'S NOTE: As a fair warning, half-way through writing this blog post, I realized this whole endevour of comparing the pseudocodes of two different metaheuristics might not have been such a great idea (and may have indeed been a clever act of procrastination). I still posted it online because it may still be useful for other people though, and because I'm somewhat interested in metaheuristics. I also kept my "conclusion" footnote where I came to my realization about exactly how much time I wasted.

I've really enjoyed reading the book [Essentials of Metaheuristics](https://cs.gmu.edu/~sean/book/metaheuristics/), by Sean Luke. It is a very good introduction to metaheuristics, the field for solving "problems where you don't know how to find a good solution, but if shown a candidate solution, you can give it a grade". Metaheuristics could be very useful for hard problems, such as [generating regexes](http://regex.inginf.units.it) or producing human-readable text.

While reading htis book, I remembered a specific idea that I had in the past that I had previously forgot about. I decided maybe to revisit that idea.

I've been somewhat interested in the idea of building a poem generator, using the book [One Hundred Billion Poems](https://en.wikipedia.org/wiki/Hundred_Thousand_Billion_Poems). According to Wikipedia:

>Raymond Queneau’s A Hundred Thousand Billion Poems or One hundred million million poems (original French title: Cent mille milliards de poèmes), published in 1961 (see 1961 in poetry), is a set of ten sonnets. They are printed on card with each line on a separated strip, like a heads-bodies-and-legs book, a type of children's book with which Queneau was familiar. As all ten sonnets have not just the same rhyme scheme but the same rhyme sounds, any lines from a sonnet can be combined with any from the nine others, so that there are 10^14 (= 100,000,000,000,000) different poems.

Obviously, you cannot read all 100,000,000,000,000 poems to find the best 'poems' to show to the interested reader. But what you could do is to come up with an algorithmic approach (sometimes also known as a "fitness function") to measure how good a randomly-generated poem could be (the "grade" that Sean Luke talked about). Then, just randomly generate a bunch of poems, compare their grades to each other, and then pick the poems with the best grade. Sean Luke referred to this approach as "random search".

Of course, random search, while effective on its own, is probably very slow. We can certainly do better than random search - and this is why the field of metaheuristics was created...coming up with approaches that may be more likely to find the best solutions to the problem.

However, at the time when I had this idea of using metaheuristics to generate poetry, I was only familiar with the most popular form of metaheuristics - [genetic algorithms](https://en.wikipedia.org/wiki/Genetic_algorithm)...and genetic algorithms required "mutation" (randomly changing one minor aspect of a candidate solution) and "crossover" (combining two different candidate solutions to create a brand new candidate solution). I'm comfortable with the idea of mutation but wasn't too familiar with how to program "crossover" within a poem (and whether "crossovers" even make sense as a poem), so I did my own search to figure out other ways of solving this problem.

Through my research, I discovered [Cuckoo Search](https://en.wikipedia.org/wiki/Cuckoo_search), a fairly recent metaheuristic algorithm discovered in 2009, motivated by a metaphor of [parasitic cuckoos](https://en.wikipedia.org/wiki/Cuckoo). This approach didn't require any sort of crossover (instead relying solely on mutation), meaning that it would probably be more suited to my approach of generating a poem than genetic algorithms.

However, I was concerned whether cuckoo search actually was "novel" (or if it is only well-known due to its reliance on metaphors to explain itself, and the algorithm could very well be simply [another, already-discovered metaheuristic in disguise](https://www.cs.ubc.ca/~hutter/EARG.shtml/stack/2013_Sorensen_MetaheuristicsTheMetaphorExposed.pdf)).

I was so concerned about this minor point that I [asked a question on CS.StackExchange](https://cs.stackexchange.com/questions/80784/was-the-cuckoo-search-independently-discovered-before-2009-if-so-what-was-th) - the response from the CS.StackExchange community was essentially: "Does it really matter?", which I have to admit is a pretty good answer.

When typing out my question, I wrote out the following pseudocode of Cuckoo Search:

1. User set the following parameters: the population of candidate solutions  to generate (n), a percentage (p_a), and the number of iterations.
2. The initial population of candidate solutions (n) are generated.
3. Several candidate solutions are randomly selected for evaluation (this selection would be done using [Lévy flight](https://en.wikipedia.org/wiki/L%C3%A9vy_flight).

4. For each candidate solution selected for evaluation:
 - Generate a new candidate solution (called NewSolution)
 - Compare the fitness of NewSolution with the current candidate solution
 - If the NewSolution's fitness is greater than the fitness of the current candidate solution, replace the current candidate solution with NewSolution
 - Else, throw away NewSolution

5. All candidate solutions are ranked, according to their fitness.
6. The worst (p_a)% of candidate solutions are discarded. The best candidate solution is saved in the variable "current_best".
7. New candidate solutions are generated to replace the candidate solutions that were discarded in step 6.
8. Repeat steps 3 to 7 until the number of iterations is reached.
9. Return "current_best".

(Sidenote: In the literature of cuckoo search, p_a is sometimes referred to as the "switching parameter". It is also possible to [vary "p_a" dynamically](https://www.sciencedirect.com/science/article/pii/S2210832717301679) as well, instead of keeping it as a static value.

I'm also not sure whether my pseudcode for step #3 is correct. It's possible that only one candidate solution is selected for evaluation in Step 3, and the **generation** of the canddiate solutions (both in Step 4 and in Step 6) is done using Lévy flight.

Also, I'm pretty sure you could replace Lévy flight with [Gaussian Distribution](https://en.wikipedia.org/wiki/Normal_distribution), and indeed, [a peer-reviewed article](http://web.info.uvt.ro/~dzaharie/ma2017/projects/techniques/CuckooSearch/CuckooSearch3.pdf) claimed to have made this substitution successfully.

The fact that I'm not quite so clear about the details of "cuckoo search" is probably a good argument for me not to use it. I've read "pseudocode" (and actual code) of several different implementations of cuckoo search and am still fairly confused as to what it is. Then again...does it really matter whether I'm following the 'proper' pseudocode? If it works...it works.)

Of course, having discovered this potentially useful approach to generating poems, I promptly forgot about this idea. I did eventually come back to it though after discovering and reading through Sean Luke's [Essentials of Metaheuristics](https://cs.gmu.edu/~sean/book/metaheuristics/).

Sean Luke did not mention "cuckoo search", but he mentioned many other metaheuristics that are older and more popular than "cukoo search", many of whom also doesn't require crossover. One of those algorithms is [Evolution Strategies](https://en.wikipedia.org/wiki/Evolution_strategy), an approach developed in the 1960s that was recently used by [OpenAI](https://blog.openai.com/evolution-strategies/) to improve the performance of reinforcement learning networks.

The pseudocode for the simplest form of Evolution Strategies (the "(μ, λ) algorithm" as Sean Luke called it) is as follows:

1. User sets the following parameter: the initial population of candidate solutions to generate (λ), the number of candidate solutions to keep after each iteration (μ), and the number of iterations. λ must be a multiple of μ.
2. The initial population of candidate solutions (λ) are generated.
3. All candidate solutions are selected for evalution.
4. The best candidate solution is saved in the variable "current_best". The best μ candidate solutions are kept, while all other solutions are deleted.
5. Each of the μ candidate solutions gets to generate λ/μ candidate solutions through an ordinary mutation (a copy of the fit individual is made and then mutated). This means that a total of λ new candidate solutions get generated.
6. Repeat steps 3 and 5 until the number of iterations are reached.
7. Return "current_best".

It seems that the (μ, λ) algorithm is very similar to that of Cuckoo Search, with Cuckoo Search's "p_a" being the inverse of "μ" ("p_a" specifies how many candidate solutions die, while "μ" specifies how many candidate solutions lives).

The only main difference between Cuckoo Search and the (μ, λ) algorithm seems to be the existence of Cuckoo Search's Step 3 and Step 4. A random candidate solutions is generated and could potentially replace a existing solution - right before a general purge of all "weak" candidate solutions commence. This means that slightly more candidate solutions could wind up getting generated  and terminated under Cuckoo Search than under Evolution Strategies.

I think that this difference may very well be minor. While I still like the ideas behind cuckoo search, I would probably prefer using the (μ, λ) algorithm instead (due to the fact that it has been used for much longer than cuckoo search and there's probably more of a literature behind it). Alternatively, I could also use another metaheuristic approach that doesn't requires crossover (such as [Hill-Climbing With Random Restarts](https://en.wikipedia.org/wiki/Hill_climbing) or [Simulated Annealing](https://en.wikipedia.org/wiki/Simulated_annealing)).

<hr />

And...after spending 2 hour writing and researching for this blog post (which I thought would "only" take me 30 minutes), I realized that I probably wasted my time. While I like learning multiple different ways of solving the same problem, in the grand scheme of things, it probably doesn't really matter what approach I take to generate poetry. Just pick one and go with it. Different approaches may come up with different solutions, but we probably won't really care about finding the most "optimal" poem out there - finding one human-readable poem is good enough.

Besides, most of the literature about metaheuristics assume that you already have a good way of testing how good your candidate solutions are. But...er...I haven't actually came up with said test yet (instead procrastinating by studying metaheuristics). Even if I do come up with that test, other people may not agree with that test (as they may have their own unique tastes about poetry). We can't really reduced poetry (or indeed, any form of text generation) down to a simple fitness function...and it may take many fitness functions to fully describe all of humans' tastes.

I suspect using metaheuristics to generate text will likely involve 90% "construction of good fitness functions to appease human's tastes", and 10% "picking a metaheuristic, fine-tuning it, and then running it to find a poem that passes your fitness functions". So the real lesson of this blog post is to be a bit careful about 'diving deep' into a topic. You might very well be distracting yourself from what really matters.

P.S.: While I was doing research for this blog post, I found out about ["When One Hundred Million Million Poems Just Isn't Enough"](https://infinityskitchen.com/issue-08/100-million-poems.html), which contains a generator consisting of 18.5 million billion poems (ignoring the color of those poems). Another interesting corpus for me to look at and potentially use.