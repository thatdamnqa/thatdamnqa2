---
layout: post
title:  "We depend on Acceptance Criteria too much"
date:   2018-01-23 00:00:00 +0000
categories: blog
starred: starred
---

In the last year or so, I realised that perhaps we might be relying on acceptance criteria too much. Doing so can be dangerous; it can easily lead to checkbox testing, and it can lead to the tester (and even the developer) not thinking at all.

That's not to say that we shouldn't use ACs: let me explain.

### We're writing down things that we don't need to write, just for the sake of writing it down


I think that ACs should be high level. They're the things that the product owner (or customer) cares about. For example, they want to increase sales of a widget, so in order to do that they want a hero image on their homepage to advertise their sale of widgets. So the acceptance criteria would be there's a hero image (widget-sales.png) on the homepage which links to the widgets page.

If there are already hero images on the site (or even if this is replacing an existing hero image), then there's certain things that can be taken for granted which simply don't need to be stated.

We don't need to know what the size of the hero image should if it's the same as every other hero image on the site because it can be assumed knowledge.
As can the behaviour if the site is responsive (does it resize or are other images displayed on smaller screens).
As can the alt text of the image, if this is something provided by the copywriter alongside the image itself.

If we include all of this information, we've fallen into the trap of checkbox testing. We're writing down specific things to check where instead these are things that are checked as part of the greater ticket. We're writing things down that are already obvious, that will be provided as part of design docs, that are part of domain knowledge.

I'm not saying "don't write anything down". I'm saying don't write down things that are already part of domain knowledge, already provided elsewhere, or are obvious.

### We're taking decisions away from developers and testers and expecting the product owner to make them all, even when it's not their areas of expertise

As I said, ACs are things that the product owner actually cares about. If we return to our widget hero image example again, all the product owner cares about is "I want to sell more widgets, so I want a hero image on the homepage that will take the user to a page where they can buy widgets".

They probably don't care how it looks: that's for the designer to decide. They don't care how you make the image accessible, as long as it's accessible: that's for the developer/UX people to decide. They don't care whether the hero image uses Javascript to load the page, or whether the image should be hosted on a CDN: these are decisions best made by the developer.

If we expect the product owner to answer these questions while writing the ACs, then we expect the product owner to have the answers; where usually they aren't in a position to know them (or don't have any strong opinions). If we leave them out of the acceptance criteria, we're giving the designers, UX people, developers, and testers the freedom to do what they feel is best.

That's of course not to say that the product owner can't have an opinion — and these can be expressed in the work ticket — but they shouldn't be part of the formal acceptance criteria.

That's also not to say that if the people implementing the body of work isn't sure they can't ask the product owner. As a tester, if I'm unsure how something should act, I can always go to the product owner and ask. Because ACs aren't a replacement for communication.

### The acceptance criteria aren't a list of tests

Once we write down acceptance criteria, we fall down the trap of a non-tester thinking "well this is what I need to do in order to have a working solution". Developers will stop thinking of edge cases. And the people testing the feature — especially if they aren't testers — will test nothing else. They won't read between the lines, and they'll only follow the happy path. They'll start checkbox testing.

They should also never be used as some kind of log of "what's been tested". Because it will always be incomplete. There are always things that we, as testers, always do that we just don't think about. There are always extra things we check, outside of the acceptance criteria. That's not to say we shouldn't make a note of things we've checked: this can be an appropriate thing to do. But if we do, they aren't acceptance criteria.

### The acceptance criteria isn't documentation

We shouldn't have ACs as documentation, either. And it would be dangerous to think otherwise. This is what a ticket is (or at least, should be), at a given point of time, independent of every other feature (implemented or planned).

The feature might later change, or the site might later change. For example, if the AC for calculating the price of a shopping cart says "It should be the price of the product, plus 20% VAT, plus £5 shipping charge", this will no longer be documentation if the VAT amount has changed, or after the shipping charge is removed.

### You can never have a full list of acceptance criteria, anyway

To expect to have a full list of acceptance criteria would be a fool's errand. There's always more things that you can test. There's always things you can ask. There's always assumptions that can be made. To write down all of these assumptions and questions would be a waste of time: especially when the answer is already known.

### So let's start being selective

Let's start being selective on what our ACs say. Heck, let's start being selective over whether a ticket has AC at all. If we're writing things in a ticket just because process says we should, are we really following an agile workflow, or are we just blindly following process without questioning it?