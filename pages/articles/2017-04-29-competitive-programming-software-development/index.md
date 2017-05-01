---
title: Competitive Programming and Software Development
date: "2017-04-29"
layout: post
path: "/competitive-programming-software-development/"
category: "SoftwareDevelopment"
description: "In which I compare and share some lessons learned about competitive programming and software development."
---

Programming challenges have recently been the source of much contention in the tech world. This is because they have been co-opted by companies as a component of their interview process for coding roles<sup>1</sup>. Competitive programming has been roped into the discussion because these challenges usually contain problems similar to those found in competitions like [Google Code Jam](https://code.google.com/codejam/) and [ACM-ICPC](https://icpc.baylor.edu/). 

Success in these competitions typically requires knowledge of theoretical computer science material like data structures, algorithms and computational complexity analysis, and occasionally topics from mathematics such as number theory and combinatorics. It also requires the ability to apply this knowledge to come up with algorithms. 

The arguments (and they're usually arguments) mostly center around the thought that it isn’t clear how effective these challenges are as a predictor of job performance<sup>2</sup>. It’s pretty difficult to find a discussion about tech interviewing, and increasingly competitive programming, without mention of how broken interviewing is<sup>3,</sup><sup>4,</sup><sup>5</sup>. A common argument I’ve heard is that these questions test Problem Solving Skills™, but the implications here are that these are the same skills employed in developing software and that these skills make you a better developer, neither of which is immediately obvious.

I’m not certain whether there is a one-to-one translation between these two skillsets but I can’t agree that they’re completely divergent either. Here are some of my thoughts about the overlap, based on my (admittedly limited<sup>6</sup>) experience in both competitive programming and software development:

1. **Knowing your language** - It helps to learn your preferred programming language in depth to improve as a competitor and a developer. Different programming languages have their own paradigms, features and idioms that help when solving common problems. Knowing these lowers the bar for understanding other people's code and trying to get help with your own. Additionally, knowing the language’s standard library and how things like big numbers are handled ends up saving a lot of debugging time. A caveat here is that most competitive programming questions are designed to be solvable by any turing-complete language<sup>7</sup>, so knowledge of some language features that amount to syntactic sugar may not help much. 

2. **Efficiency and completeness are important** - Competitive programming forces you to include “efficiency” and “completeness” in your definition of “correctness”. If your algorithm doesn’t pass all test cases because it timed out or missed an edge case, you won’t receive maximum points. The time complexity and extreme cases of your algorithms can’t be an afterthought. In other words, "It worked! Next problem!" is immediately not good enough for most programming competitions. Whereas, in other cases it may only be necessary to consider efficiency when faced with hardware limitations or similar constraints. Missing an edge case in a software project can also mean an app crashing or a user losing some data. I think the benefit here is that this conditions you to scrutinize your code a little more in search of these optimizations and edge cases. However...

3. **Efficiency is not always important** - Many developers will never have to worry much about efficiency<sup>8</sup>. In many cases, the libraries and algorithms you use have already been optimized and you simply glue provided APIs together. It might also be counterproductive (read: detrimental to your bottom line) to spend too much time on the efficiency of your code if speed of delivery is the main metric by which your performance as a developer is appraised. Your time may be better spent making it work, making it right and only then, making it fast<sup>9</sup>. I've noticed that in competitions the bulk of my time is spent trying to come up with an algorithm that isn't an exhaustive search of the solution space, but on long(er) projects it's spent ensuring that people will actually be able to understand my code quickly. Which leads me to...

4. **Readability** - On any software project, a developer has the overhead of learning the existing codebase if one exists. If that code is opaque to everyone except the original author, then the time required for others to ramp up is much longer. This translates to more hours spent before the point of productivity is reached. Practically, optimizing for readability<sup>10</sup> means doing things like not writing functions that do too much on their own, using well-named variables and minimizing cyclomatic complexity. In competitive programming however, readability is usually the last thing on your mind<sup>11</sup>.

5. **Context** - Some competitive programming questions rely on “realistic” stories which can act either as a layer of misdirection or a helpful visualization, depending on the author (and reader). This can make it more difficult to discern the actual problem<sup>12</sup>. Additionally, the motivating context of a specific learning goal or a larger project just isn't there when reversing a linked list<sup>13</sup>. 

6. **Time pressure** - Programming competitions tend to have time limits of one or a few hours. This doesn't help otherwise capable people who don’t perform particularly well under pressure. I’ve found that when I’m stuck on a problem, it helps to take a walk or do something unrelated (and not cognitively demanding) for a while. That might not be possible when you’re running out of time and everyone is panicking<sup>14</sup>, but entirely possible when working on a long term software project.

7. **Rigor** - A major reason I bother with competitive programming is that it almost always results in my having to sit down and just think really hard<sup>15</sup>. In that way, it reminds me more of doing problem sets from math courses and theory of computation, than it does of software projects. I’ve found that my software projects tend to be more so exercises in creativity and research with occasional, challenging algorithmic problems. There are two kinds of "difficulty" at play here.

There’s more to say about this topic, but I’ll end with a basketball analogy. I don’t expect to get better at full court 5 on 5 by shooting free throws. My coaches always told me to train like you’re in the game so I’ll echo that advice: if you want to get better at programming competitions, you should compete a lot. If you want to improve as a software developer, build a lot of software. Also If you ever see me starting for the Lakers you can assume I placed first in {insert international programming competition here} the night before. Please don’t hold your breath.

Notes:

[1] - I’ve mostly seen mention of programming challenges for roles with titles like: Software Developer, Front-End Developer, Software Engineer, Backend Developer, Web Developer.

[2] - In fact, there may be evidence that it's a negative indicator. [Here](https://www.youtube.com/watch?v=DdmyUZCl75s) is Peter Norvig, a director of research at Google. Full talk [here](https://www.youtube.com/watch?v=T1O3ikmTEdA).

[3] - See multiple comment threads on this Hacker News [post](https://news.ycombinator.com/item?id=14071971) on the last question in the Google Code Jam qualification round discussion.

[4] - [A tweet by Max Howell, author of the Homebrew macOS package manager](https://twitter.com/mxcl/status/608682016205344768) 

[5] - [A tweet by David Heinemeier Hansson, author of Ruby on Rails](https://twitter.com/dhh/status/834146806594433025)

[6] - I don’t purport to be an expert in (or even particularly good at) either competitive programming or software development. I first heard about competitive programming while in my second year of university and competed in the ACM-ICPC, IEEExtreme and Google Code Jam with little practice. Much of my software development experience has been personal and school projects as well as contract web development. If you were seeking opinions forged in the crucible of many years experience, [I’m sorry but](https://www.youtube.com/watch?v=532j-186xEQ).

[7] -  And I mean any. Seriously, choose an esoteric programming language and search through hackerrank solutions if you want a good laugh (I recommend lolcode).

[8] - Or about reversing Linked Lists. Why is this not on a shirt yet?

[9] - As is the [Unix way](http://wiki.c2.com/?MakeItWorkMakeItRightMakeItFast).

[10] - I think the authors of The Structure and Interpretation of Computer Programs said it [best](https://mitpress.mit.edu/sicp/front/node3.html): 
> Thus, programs must be written for people to read, and only incidentally for machines to execute.

[11] - Interestingly, there is a meta-competition among the more experienced competitors in which they try to write the shortest, most clever solution. This is often done using complex lambdas which tend to be visually dense and hard to parse(sorry). 

[12] - I have heard though, (and I can’t remember where) that higher level competitors ignore the preamble. If this is true, the fact that I read them all is quite telling… 

[13] - Seriously. I’d wear it. In public.

[14] - To be fair this can happen on software projects too. My point is that I think “works well under pressure” is  something a competitive programmer can say with conviction in an interview. 

[15] - See: [The Feynman Algorithm](http://wiki.c2.com/?FeynmanAlgorithm).
