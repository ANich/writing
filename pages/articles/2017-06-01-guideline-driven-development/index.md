---
title: Guideline-Driven Development
date: "2017-06-01"
layout: post
path: "/guideline-driven-development/"
category: "SoftwareDevelopment"
description: "In which I talk about my almost loveless relationship with coding best practices."
---

 
I like to occasionally pause and reflect on the “meta-aspects” of programming, specifically how I myself write code. I try to think about things like: how often I write code, what kind of code I end up writing, how much time I spend changing old code vs. writing new code, etc. I’ve recently been thinking about a habit that appeared when I started moving past the basics, and that I’m increasingly wary of nowadays.
 
When I first started writing code, the only thing that registered was whether or not my code did what it was supposed to do<sup>1</sup>. In order to write more interesting programs though, I had to start doing two things that changed what mattered: start working with other people and think more about my methodology so I could optimize how I spent my time. Coincidentally, this was at about the same time that I started learning about the origins of modern computing and programming through my university’s *Computing and Society*<sup>2</sup> course. At the intersection of all of these, I started to think seriously about what the “right way” to write code was. Before each new project, I would research (read: obsess) about the relevant programming practices that were used by individuals and teams on big projects, stood the test of time, and had fervent individual and community support. 
 
These practices usually aren’t hard to come by if you’re looking (and sometimes if you aren’t). They come in the form of style guides, idioms, design patterns, architectural patterns, etc. 
 
For context, here are some of the practices I’ve had experiences with. These examples are taken from different subfields of development so I hope at least one will be relevant to you. 
 
### Object-Oriented Design Patterns 
 
One of the most frequently recommended books for software engineers is [*Design Patterns: Elements of Reusable Object-Oriented Programming*](http://wiki.c2.com/?DesignPatternsBook). It was written over twenty years ago by Erich Gamma, Richard Helm, Ralph Johnson and John Vlissides, often called the [Gang of Four](http://wiki.c2.com/?GangOfFour). Twenty years is eons in technology years, but it remains one of the most relevant resources on object-oriented architecture. Throughout the book, the GoF describe design patterns that fit different categories of problems that you’ll encounter when building large systems. For example:

Using the Factory Pattern, a `ResponseFormatterFactory` would be an object that creates the appropriate `ResponseFormatter`. Your classes `JSONResponseFormatter` and  `XMLResponseFormatter` should both implement a single interface: `ResponseFormatter`, so that wherever you need a `ResponseFormatter`, you can employ your factory to create the appropriate implementation based on either input or configuration at runtime.
 
Honourable mention to the [SOLID principles of object-oriented design](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)), some of which are readily applicable outside of object-oriented design.
 

### Idiomatic Python code
This generally means code that exploits the features of the Python programming language, and that is congruent with the [Zen of Python](https://en.wikipedia.org/wiki/Zen_of_Python)<sup>3</sup>.


Python has interesting constructs like:

```python
for item in sequence:
  # Do things with an item
else
  # Do things when the loop has ended… (if no break was used) 

...
 
with (expression_creating_object_that_requires_setup_and_teardown) as name:
  # Do something with name without explicitly including setup and teardown code.
 
```

In these examples, `else` can replace having a flag that tests whether some condition has been achieved within the loop, and `with` allows you to push the setup and teardown code to a [Context Manager](https://docs.python.org/2/library/contextlib.html).

Idiomatic Python tends to read much like natural language and is meant to be easily understood. Two great sources are the [Hitchiker's Guide to Python](http://python-guide-pt-br.readthedocs.io/en/latest/)<sup>5</sup> and any of Raymond Hettinger's talks.
 

### Pandorable code

Pandorable code is more or less an extension of idiomatic Python code for the pandas data analysis library. 
 
One example of writing pandorable code is ensuring that you use pandas and numpy operations as the preferred method of manipulating, grouping and aggregating your data, as opposed to using series and dataframes purely as intermediaries or containers while performing data manipulation using loops and the usual Python arithmetic and string operations. The numpy library  emphasizes efficiency through vectorization and parallelization and has been fiercely optimized, so pandorable code takes advantage of this: 
 
Assuming you have a dataframe with a Price column:
 
```
total = 0
for price in df['Price']:
    total += price
```
vs. 
```
np.sum(df['Price'])
```
On my machine, this had a difference of 527 µs vs. 57.2 µs (~10x difference) with a dataframe with 6196 rows.
 
Almost in contrast to the above, pandorable code also embraces the idiomatic Python preference for readability above most other things (occasionally including performance). 
 
```
(df.where(df[‘AGE’]>21)
    .dropna()
    .set_index(['NAME','STATE’])
    .rename(columns={'FIRST': 'FIRST_NAME’}))
 ```
which is slightly slower than if you were to do each modification separately, but is a lot more "skimmable".
 
### React container components vs presentational components 

React is a JavaScript library that lets you write user interfaces for applications in terms of components that you define individually and then compose. One particular approach to using React is splitting your components into ones that are solely presentational, without state or application-specific logic and container components that specify what these presentational components do:
 
```
const styles = {...}
const NewButton = (props) => (
  <button style={styles} onClick={props.buttonClick}>New</button>
);
 
…
 
class ButtonContainer extends React.Component{
 
  handleClick () {
    // Do NewButton things...
  }
 
  render() {
    return(<NewButton buttonClick={this.handleClick} />);
  }	
}
 
```

 
The benefits accrued from applying these and other guidelines vary from case to case but here are some of the concrete positive outcomes I’ve observed from actively seeking out and attempting to follow them:
 
1. They have at times improved the quality of my code in terms of efficiency, readability, extensibility.
 
2. They provide a roadmap of sorts for you and your team when solving recurring problems, both in the cases of extending old code and writing new code. 
 
3. It is tempting to transfer previous knowledge from one framework and language, but one language’s commonplace can be another language’s anti-pattern. Seeking out guidelines helps you avoid this trap. 

4. I found the more involved and experienced programmers<sup>6</sup> in various communities. They are usually good sources of information about bleeding edge tech as well as new and old methodologies. 


While this all sounds very positive and you should definitely stand on the shoulders of giants, this is also a cautionary tale. Here are my cautions<sup>7</sup>: 
 
1. Sometimes there just isn’t a best practice for what you’re trying to accomplish. Your best bet may be to dive into some source code or to just start something. Sometimes you just need to ship and iterate.
 
2. Depending on the technologies you work with, things can move very quickly in the software world. Today’s best practice may become outdated tomorrow<sup>8</sup>.
 
3. There’s also a slippery slope which can lead to over-engineering. You can turn your code into a terrifying mishmash of design patterns<sup>9</sup>, that doesn’t actually do much.
 
4. For certain personalities, it may be easy to fall into the trap of philosophizing more than actually implementing<sup>10</sup>. 
 
I still try to seek out these best practices whenever I’m exploring new technology, but now I try to err on the side of shipping earlier rather than later if possible. There will likely be a chance to refactor if something better comes up. 

> "Le mieux est l'ennemi du bien" \- *Voltaire*

*Transl: The perfect is the enemy of the good*

As a sort of post-hoc benefit: now that I've stopped spending so much time looking for guidelines, I've started to develop my own architecture using the same philosophies that underlie most guidelines (namely: extensibility, readability, clear separation of concerns, etc.), and I think I'm better of for it.
 
[1] - On a lot of projects this is still the only thing that matters to me. For example when I'm trying out new technologies.

[2] - [Big up](https://www.mona.uwi.edu/compsci/comp1220)

[3] - You can also type `import this` in a Python shell to see the Zen of Python.

[4] - Some people will tell you "expression_creating_object_that_requires_setup_and_teardown" is how I actually name variables. These people are correct.

[5] - These people *really* know where their towels are. 

[6] - These are also likely to be the authors of the languages/frameworks/libraries that have guidelines.

[7] - He said reluctantly adding another list to this post.

[8] - Anyone from the JS world remember writing immediately invoked function expressions to create your revealing modules? No? Ok.

[9] - A la [Enterprise Fizzbuzz](https://github.com/EnterpriseQualityCoding/FizzBuzzEnterpriseEdition).

[10] - [One of my favourite related pieces on this](https://blog.codinghorror.com/are-you-a-doer-or-a-talker/) by Jeff Atwood.