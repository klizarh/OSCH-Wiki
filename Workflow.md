# Major Links:
* Root organization page on github - [here](https://github.com/futureag)
* where ui gets deployed - [here](http://futureag.netlify.com/)
* place that generates the public-facing site - [here](https://github.com/futureag/blog)
* the publicly generated site hosted on gh pages - [here](https://github.com/futureag/futureag.github.io)
* finally, public site - [here](https://futureag.github.io/)

# To Start

Everything should flow through a [single project](https://github.com/orgs/futureag/projects). The project is arranged to look like this:

[pic here not sure how to add yet]

* **Idea Stockpile** - aka, backlog. This is the dumping ground for everything.
* **Groomed** - once a given card has been actually discussed, fleshed out, and scoped out by all the relevant parties, it can move into this column.
    * ui mocks
    * api schema agreements
    * business concerns
    * etc
* **To Do** - Every sprint, we'll pull stories out of the groomed column and into this one. This means they're ready to be worked on.
* **In Progress** - these are currently being worked on.
* **Done** - these are deployed. We can add in a "qa" step later if we really want to, but to start, I'd suggest that further modifications and even bug fixes be treated as "improvements" and go through the whole flow again.

How this flows into issues:
* Improvements and Stories start out as cards in the idea stockpile.
* Bugs, and other things that naturally makes sense to file as issues start in whatever repo and get pulled into here.

# Grooming

This is where we keep everything straight. This is the part of the process that is the easiest to skip, and the most important not to. If we don't do grooming properly, all estimates and planning are off and we're better off not trying to saddle devs with a process they're going have to work _despite_, instead of working _because of_. So if we don't do this, and we don't do it well, it's probably better to throw everything out. This is the place I've seen the most people mess up.

* All relevant parties must have been consulted for a ticket.
* Tickets that start as a card must spin out into sub-issues in the relevant repos
* Tickets that start as issues must be pulled in

A properly groomed ticket must include:
* all problems, broken down to the level of abstraction that makes sense to the SME
* each of these sub-tickets must contain
    * links to all relevant resources
    * a yes-or-no way to determine if the ticket has been accomplished (acceptance criteria)
    * the ability to quickly, for any ticket, figure out what job story it belongs to
* Lastly, we'll be using some sort of definition of done. for now this could just mean 'working', but later could include:
    * testing
    * documentation on wiki
    * some sort of qa
    * etc

# Opening a Sprint
To open a sprint, we'll [create new milestones](https://github.com/futureag/ui/milestones) in relevant repos.

[milestone picture]

Then we link the issues in the sprint (which are also in the To-Do column). Each sprint will have its own set of milestones, and then git will pretty much track everything else for us automatically.