---
title: How I Claude
tags: [delve]
---

I am a programmer. I _love_ writing code, at least in Ruby; it's my craft, and I find a lot of enjoyment
in building the abstractions and polishing the surfaces and shape of my code until it gleams. So I have been..
fairly concerned over the last year or so as the actual effectiveness of LLM code-generation has improved.
Will companies stop wanting to pay me lots of money to do things I enjoy doing? Is the industry evolving away
from the need for large numbers of people like me? How worried should I be, financially speaking?

And the answer is.. yeah, a bit. In my day job, I'm using Claude Code pretty substantially, but I'm still
_responsible_ for everything I commit and do, and I'm still involved in the code itself - reading, polishing,
reviewing, suggesting. And that's a _bit_ less engaging, it's true. My review-to-write ratio is way higher than it
used to be, and reviewing code is not the most fun part of engineering. In Delve, I've taken that quite a bit
further - I am not reading or writing **any** of the code here directly; I'm serving as an architect, a product
manager, a project manager, and a tactical lead; Claude is filling the roles of engineer, test-engineer, QA,
and (loosely) designer. I actually enjoy architectural decision-making and game design as well, or this would
probably be very unpleasant.

## The Implementer

I use Claude in several distinct ways and workflows, and they're worth thinking about separately. First, Claude
is an implementation engineer - it has been told to build things with tests, to verify them in a browser, to ask
questions and track decisions that it made for my review, and it's not bad at this. Implementing individual
features generally goes pretty smoothly; I frequently need to point out awkwardnesses or tell it to search for
existing examples of a feature to prevent it from trying to _guess_ algorithms and techniques - it usually
invents something that works alright, but has a bunch of issues; trying to construct the 'obstructing hull' of
a 3d object, for example, it came up with a mediocre solution that wasn't very performant, and when I asked it
to summarize the prior art and existing approaches, it _immediately_ saw published algorithms that do the same
thing, but better and faster.

As an implementer, Claude (and likely any other LLM) has some strengths and weaknesses. It's good at tracing
calls, and writing unit tests and functional interfaces. It effectively has a basic understanding of _so many_ topics
that I lack (3d rendering, sound design, skeleton-backed modeling and animation, file compression techniques,
the list just gets longer over time). And it's tireless - I can set it to work a dozen different tickets, then
go to bed; in the morning I have 8 PRs, 3 blockers to talk through, and one ticket where I misunderstood the
context, and my requirements don't actually make sense. The amount of progress I can make when I only need
to understand the _concepts_, and not learn the programming APIs or write the code and tests myself, is really
astonishing.

The problems are also interesting - the first one is that Claude _doesn't feel pain_. When it works on tickets,
the higher-churn code it's touching is getting _steadily worse_, because Claude never reaches for a thing,
recoils in disgust, and starts refactoring it so it can stand to keep going. I needed to add explicit paydown
phases to my milestones, and construct skills oriented toward finding the missing abstractions, examining and
improving the high-churn code, and recognizing the symptoms of painful coupling. And it's _not bad_ at that, as
long as I tell it to do it.

The second major weakness (as an implementer) is that Claude _doesn't feel pain_ - specifically, UX pain.
When it builds a feature, as long as it's _possible to do the thing_, the feature is right. It doesn't
recognize that clicking through 6 options every time you add a unit is a problem, or that having to individually
select 80 objects to add them to a template takes too long.

And the third issue is that it's very obedient. One of the more critical parts of the interaction between a
product manager and the engineers they're working with is that, when a PM asks for something that doesn't
match the existing abstractions, good engineers push back - they point the mismatch out, describe what would
need to change, question large efforts for small gains, and propose alternative approaches that would fit
the data and/or code better. Claude does do that, but generally only when it sees that the existing code
clearly had _intent_ that doesn't match the new request; it's not great at using effort-costs to recognize
poor fits.

## The Researcher

The second way I use Claude (well, the _first_ way when I'm doing things right, really) is as a technical
researcher. When I hit a harder problem, like rendering performance, pathing, concurrent access patterns,
landform tooling, creature design, etc., I have learned not to just have Claude make decisions or suggest
ideas; instead I ask it questions designed to pull the "standard approaches" and prior art into the
context: What other games have systems like this one? How do they do things? Is there any existing research
on this topic? The answers to these questions usually help _me_ understand the problem domain better, and
also steer Claude away from trying to guess a solution when other teams have already iterated and found
solid answers.

Alongside its ability to dig through piles of references and find relevant comparisons, Claude is good at
processing data. Existing games often have a lot of information available - how much damage various classes
do at various levels of various games is publicly discussed (**excessively** discussed, usually); geographical
information about zones and spawn locations is also out there. So as I'm working out combat balance, I can
use the immense amount of research and iteration other teams have already gone through to inform my target
numbers; I can see how far apart other games typically space their quest hubs, how much travel is expected
by a typical quest, how quickly units should die to feel like a challenge but not a deadly threat. Even
better, the process of analyzing and collating that information turns it into something Claude is able to
_work toward_ fairly readily.

## The Secretary

I am _deeply_ ADHD, and while that can mean a lot of things, my primary impacts are executive dysfunction
and a combination of hyperfocus and scattered attention. When it comes to getting _one thing done_, I am
extremely effective (though I may forget to eat or accidentally go to bed at 4AM). But a project like Delve
involves tracking _hundreds_ of things, and making sure to stay focused on the current milestone without
losing all of the intention I form constantly as I work on and test the application. There are literally
thousands of tools for those purposes; this is a difficulty that every organization faces. But adding
executive dysfunction to that organizational challenge creates a set of problems that I _used_ to overcome
by constructing elaborate and gamified systems to manage my attention and track my work. Claude does a
better job of that - I keep a `meta` session open, and that session is where I add issues, change/create
milestones, discuss issue interdependencies, and file bugs for myself. (And also prompt me to write blog
posts when it sees potentially interesting topics being completed).

To be clear, Claude is _not_ as good as an actual person dedicated to that purpose, and CEOs won't be
firing theirs. But it's **way** better than post-it notes stuck to my laptop and 30 slack-reminders telling
me to "track __ as an issue". And because I have it using GitHub Issues to track that information, it's
easily browsable and commentable with context that would otherwise fall out of my attention and be lost
in the mists of my terrible memory.

## Who Am I Then?

So.. while I am building this game, I'm not really _writing_ it. And perhaps I will eventually regret
that? But probably not; this thing is becoming interesting and playable _very_ quickly, and I'm learning
an incredible amount about diverse topics as I go. I haven't been this engaged in a software project in
quite a long time, even though I'm not actually performing one of my favorite activities as part of it
at all.

Will it be successful, maintainable, interesting to others? I have no idea! And if I were spending
years on this, that would weigh on me - the possibility that all of this is wasted, and that nobody will
care. But.. it's only been a few weeks, and it's been so _approachable_; I think that if nobody ever
plays this game, I won't even feel bad about it.
