%title: TIPS ON DEVELOPING LARGE (AND SMALL) SOFTWARE PROJECTS
%author: chandler
%date: 2021-04-26

-> TIPS ON DEVELOPING LARGE (AND SMALL) SOFTWARE PROJECTS <-
=========

-> Best practices, source control, debugging. <-

-------------------------------------------------

-> # Overview <-

1. PLANNING
   ^
2. CODING
   ^
3. VERSIONING
   ^
4. DEBUGGING
   ^

-------------------------------------------------

-> # 1. PLANNING <-

Planning software projects is a daunting task. One that gets
even more overwhelming when they are interactive, works of
art, games, etc. But knowing a few tried and true places to
start can help.

-------------------------------------------------

-> # 1. PLANNING: THE ACTORS <-

I don't like the word "user." Silly perhaps, but I strongly
believe that words matter, and that the ideas (metaphors) we
use to think other ideas should never be taken for granted.
This is also true when thinking of what you call the
person(s) who encounter your work of art or design. Anyway,
for this discussion, I'm going to use the word [PUBLIC](https://press.princeton.edu/books/paperback/9781890951290/publics-and-counterpublics)
in place of user.

The main motivation here is that you can consider your
software to have a front and back, a side visible to outside
world and one behind, the source, the "system." I find this
to be a useful distinction because it gives you a framework
to help articulate the problems you need to solve.

Our main actors then, the *public*, and the *system* (There
is of course a third actor, you, your motivations, and needs
for the software, who is central, but we will table that for
now.).

There a few main things to keep in mind about our actors:
- what do they *know* and need to *know*?
- what are they *doing*?
- what are they *experiencing*?
- and how can they *act*?

-------------------------------------------------

-> # 1. PLANNING: THE PUBLIC <-

When thinking from the side of the public, begin by
imagining, step-by-step, the experience of someone
encountering the software. What is the first thing they
experience? Sound, color, interface, etc. Then what do they
do/experience? And so on and so on. The philosopher Daniel
Dennett has a idea that is something like, "Every organism
is always asking and answering the question, 'What do I do
now? And now? And now? Forever.'" Considering the experience
of your work from the perspective of the public helps you
conceptually and technically (this is true of software and
paintings and sculptures, etc. For the purposes of this
discussion however, it gives us a framework to hang our
thinking on. Because the question "what do i do now?" is
going to be asked of the software you are writing. Do I
click a button? Upload an audio file? Sit back and relax?
Plug in my headphones? As someone writing software, you are
providing the potential range of questions and their
answers.

This covers most of the *doing*, *experiencing*, and
*acting*, but don't forget the *knowing*. Knowing is a harry
concept, and i'm going to use it a bit loosely here, tho i'm
always up for talking about knowledge and meaning formation,
just hmu. Anyway, we can apply questions about the public's
knowledge at a number of scales from the technical to the
conceptual. Who made this? How do I move? What file formats
are valid? WHAT IS HAPPENING AND WHY AM I HERE?

-------------------------------------------------

-> # 1. PLANNING: THE PUBLIC <-

Think about the experience of using your software, and write
down a narrative of this experience. This will give you a
map of what you need to implement to provide that
experience. Be as careful and detailed as possible, paying
extra close attention to what they must *know* in order to
act in a meaningful way. Knowing is extra slippery here
because [you often don't know what you know](https://www.youtube.com/watch?v=ql80Klk4pSU). The
slipperiness of knowing expresses itself on all levels, e.g.
taking for granted familiarity with WASD, assuming the
public is familiar with a particular thinker, concept, or
history, or mistakenly presupposing their commitment to and
belief in your ideals.

-------------------------------------------------

-> # 1. PLANNING: THE SYSTEM <-

This great thing about this framework is that from the
system side you can ask all of the same questions! In
software dev I tend to anthropomorphize EVERYTHING.
Philosophically this is problematic as a general habit, but
for thinking about software it can be very helpful. A huge
difference on the system side however, is that *everything
can be an actor* and THE SYSTEM can (and should) be
conceptually broken into increasingly smaller components
that all have their own *knowing*, *doing*, and *acting*.
One slight modification is that on the system side we need
to be aware of what *relationships* and/or *dependencies*
components have on each other.

Much like working from the public side, on the system side
you can tell stories about what your software is doing, how
it responds, what it knows or needs to know, what it should
be preparing for, etc. Think about the narrative you wrote
in the last step, now write the same story from the side of
the system, starting with `setup()`, page load, `Start()`,
`Awake()`, etc.; whatever moment your software begins to
act. Do you need to load files from disk? From a server?
Draw some buttons? Play some music? Again be as detailed as
possible. If the public uploads a file, do you need to save
it to a server? A database? Or just hold it in memory? Ack
they moved a slider because I drew one for them, now i need
to update the color palette. That kind of thing.

*Every moment of the public story should be reflected in the
system story. The system provides the field of
possibilities, there cannot be a gap between what the public
experiences and how the system provides that experience.*

Knowing is difficult in a different way here because you
need to think about data structures. How does the system
represent its knowledge? What actors in a system have access
to that knowledge and how? Who can update it? Does it need
to be searchable?

-------------------------------------------------

-> # 1. PLANNING: YOU <-

Now for the last big step. You know what you hope the public
will experience and you know what the system will need to do
to facilitate it. You may not however know how on earth to
do many of those things. That's what we'll talk about now,
but on last note before we move on, capture all of your
questions all the time, write them down, use voice memos,
post them on forums and discord, call your friends,
[talk to stuffed animals](https://en.wikipedia.org/wiki/Rubber_duck_debugging).

-------------------------------------------------

-> # 2. CODING <-

-------------------------------------------------

-> # 2. CODING: What You Don't Know <-

It can be incredibly frustrating and overwhelming to try and
do something in code when you aren't sure how to do it. I
can say that this feeling happens less frequently the more
you code, but it never goes away 100% (but then you wouldn't
be learning which, why bother?) There are some tried and
true ways around it though. The primary and most fundamental
is community. Since this is a small group, we have some of
that built in, but of course there are others out there.
Discords for particular frameworks, user groups, forums. At
DMA the Conditional Studio discord is always open to all and
there are many of us that just love to talk about software
and problem solving, for game tech there is the Game Lab who
provides excellent resources and support.

-------------------------------------------------

-> # 2. CODING: Coding is Reading, You are a Computer <-

All of my thoughts on how to code extend from this. When you
are writing code, you are executing the code in your mind
far more times than the computer will. Remember this. You
need to make the system something that you can *think* that
you can keep in your head at one time, that you can
understand.

Be consistent in variable names, make the code legible. For
instance, make all of your boolean variables take the
format: `isActive` or `hasDefenceBuff` because then your
conditionals are easy to read. But most importantly, be
consistent.


-------------------------------------------------

-> # 2. CODING: The Smallest Difference That Makes A Difference <-

But lets step back, and consider you alone writing some
code. The first step is always to try and get a clear sense
of what problem you are trying to solve, what do you need
the system to do and in what order, and what steps in that
process are you stuck on. Now, take the bit you are stuck
with, and crack it into smaller problems. Get down to the
atoms of the problem. Now that you have a pile of particles,
put them together very slowly one at a time. Doing the
smallest thing that makes a difference, then move on to the
next tiny bit, until you really find the wall. Walls come in
all sizes, but the smaller the wall the easier to leap, and
the easier to look up on stack overflow.

Even when you know where you are going, it is a good idea to
take small steps to make sure you have a clear sense of what
is necessary and what is happening. Bugs slip in when you
make 500 changes in a go without looking and forget
everything that changed. Make many small steps.

-------------------------------------------------

-> # 2. CODING: Do Just One Thing <-

Extending the above, think of your system as composed of
actors or agents or classes or modules or components,
whatever ontology sounds coolest to you. As you make these
bits, try to make them as focused as possible, they should
do one thing and one thing well. A few actions, a bit of
knowledge, that's it. Some of these agents will most likely
be collections or directors. They bring other agents
together and organize them to work together.

Smaller agents are easier to think with. The less a
particular agent knows and does, the easier it is to
mentally model what is happening in a program. (This isn't
always true, see: everything ever written in Java)

-------------------------------------------------

-> # 2. CODING: Be Lazy <-

Good coders are lazy coders. You don't wanna write the same
logic over and over, that's so much work. If you do
duplicate the same thing in a number of places, and it turns
out to be broken, yikes, that's way more work to update all
of that code, and what if you miss one? Drama and stress no
thanks. This is often abbreviated as D.R.Y. Don't Repeat
Yourself. Anf 90% of the time it is great advice. There is
almost always a way to take a bit of logic that you need in
a few places and make it a function or class or something
that *encapsulates* that logic so it is easy to reused.

Doing this also has the advantage of making it easier to
think your code. Once the thing does what it does, you can
just assume it works just like you do with pre-given
functions. Things gotta be pretty bad if you start
questioning the `line()` function.

-------------------------------------------------

-> # 3. VERSIONING <-

[https://education.github.com/students](https://education.github.com/students)
[https://www.gitkraken.com/](https://www.gitkraken.com/)

-------------------------------------------------

-> # 4. DEBUGGING <-

  - Ever listen to Car Talk?
  - Take a walk
  - Talk to the duck

