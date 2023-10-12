---
layout: post
author: Trey
title: Adding More Into Your Project Management Process
tags: ["project management", "management", "classics"]
---

You might not expect a 16th-century satire on political theory/proto-Dungeons and Dragons campaign setting to have much to say to app developers in 2023, but people have not changed as quickly as technology has. The fictional citizens in [Sir Thomas More’s Utopia](https://en.wikipedia.org/wiki/Utopia_(More_book)) face many of the same needs that modern-day people do: adequate food, education, socializing, leisure. The island rulers engender camaraderie and survival in their people through, among other ways, a biennial rotation of agricultural duties. Team leads and project managers can map this family/work structure onto their own projects and product groups. By following More’s guide for on-agrarian-off-agrarian citizens, you will unify your team’s code style, improve code reuse, and enhance your developers’ skills and coworking habits.

The excerpt is:
	
> They have built, over all the country, farmhouses for husbandmen, which are well contrived[.] Inhabitants are sent, by turns, from the cities to dwell in them; no country family has fewer than forty men and women in it[.] There is a master and a mistress set over every family[.][^1] Every year twenty of this family come back to the town after they have stayed two years in the country, and in their stead there are another twenty sent from the town, that they may learn country work from those that have been already one year in the country, as they must teach those that come to them the next from the town. By this means such as dwell in those country farms are never ignorant of agriculture, and so commit no errors which might otherwise be fatal and bring them under a scarcity of corn. But though there is every year such a shifting of the husbandmen to prevent any man being forced against his will to follow that hard course of life too long, yet many among them take such pleasure in it that they desire leave to continue in it many years.[^2]

[^1]: I excised mention of the Utopians' usage of slavery here, partly because it is immaterial to my greater point and to save words. But I want to not remove it entirely. More created this fictional paradise and still included slavery, via 14th Amendment-esque lawbreakers or prisoners of war, revealing the darkness underlying this "Best State of a Commonwealth".

[^2]: https://www.gutenberg.org/files/2130/2130-h/2130-h.htm

Every two years new citizens from Utopian urban areas leave their city walls to travel to farms, and every two years a new crop of farmers head back to the buzz of the burbs. The reason in Utopia is simple: the corn must grow. And to grow corn, people must know how to farm it. But rotation for engineers isn’t the literal do-or-die situation of pre-Industrial societies, so the impetus might not be as clear. Indeed, too much code switching between projects will slow down development due to ramp-up time and context confusion. But there are still benefits to be gained from some regular rotation, both for the apps and for the developers. 

## Potential reuse cases 

How can code be reused, after all, if there’s only ever been one case for it? What’s the point in reusable parts and design patterns if all you ever know is the singleton in front of you? Broader horizons let you see further. But remember to link development of these shared utilities to tickets of some sort, so developers will have a concrete reference and also to be held accountable for updating the common frameworks.

## Unified style 

There’s never a single “right” way to code. "Right" depends on requirements and context, e.g., a computationally fast algorithm vs a memory minimizing one, but an agreed-upon style facilitates cleaner communication. All sorts of frictions go away: unexpected bracket locations, differing vocabulary for similar concepts, mental fatigue from translating an uncommon idiom. Rotation and a good strict linter allows for developers to come in and see firsthand the style your company adopted.

## Abstraction skills 

Clear programming comes down to editing out extraneous data usage from a function/class/module and only using what’s necessary (fewer chances for side-effects). But the opportunity might not present itself often to new develeopers with just one feature or product. Going hand-in-hand with the first benefit, once a reuse case has been discovered, the next step is to abstract it to its purest and most necessary form. Rotation allows for this framework skill development, an area lacking in some developers who might only have more decorative front-end experience.

## Better problem solving 

Quick problem solving and bug investigations can come down to remembering where you’ve seen an error before or have had a similar experience, even in wholly different product domains. Efficient elimination of possible sources is based on your history and priors. Working on multiple projects allows a developer to increase their store of known examples.[^3] 


[^3]: One of the benefits I found of working at digital agencies my first years in tech as opposed to product was the number of different codebases and domains I was exposed to. Sure, some of the code was... not well written, but at least I saw what not to do and where/why/when it went wrong.

## Exposure to coworkers 

Rotating team members between projects allows for natural exposure of your developers to different stakeholders in your organization, especially in remote ones.[^4] Crosspollination between different product groups will create new idea connections as well as creating new connections between your coworkers. For future hurdles and questions, you’ll now have more people to draw from as you’ve seen them work in the past and know immediately if their experience and knowledge will be useful.

[^4]: And companies really should be all remote if possible, if only to help with climate change. What use is "efficient watercooler talk" if the water in the ocean is boiling?


## More robust organization 

You don’t want to constrain your project by relying on one or two people to do certain tasks. Multiple people should know how, e.g., to handle a release. Developers are inevitably sick or there might be turnover or they might just be busy with other equally important tasks. Regardless, spreading this institutional knowledge out among multiple people will allow for more flexible team structures and for reducing on-ramp cost when shifting developers from one project to another.

## Summing it up

Don’t be afraid of shifting your developers between products. Humanity’s been doing duty rotations for hundreds of years. As long as you maintain some continuity in team members, there will be no institutional knowledge lost. You will improve your team’s ability to create new products and pivot between feature decisions while simultaneously strengthening your developer’s skills. All taken together, you can try to achieve Utopian app development. If it doesn’t work out, well, [tell Sir Thomas More we’ve got another failed attempt]( https://www.youtube.com/watch?v=K-P15e6NvtU).
