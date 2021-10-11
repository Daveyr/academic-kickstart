---
title: Antifragile book notes
author: ''
date: '2021-10-11'
slug: antifragile-book-notes
categories:
  - Blog
tags:
  - Project Management
  - Organisational
  - Uncertainty
subtitle: ''
summary: ''
authors: []
lastmod: '2021-10-11T14:46:19+01:00'
featured: no
image:
  caption: ''
  focal_point: ''
  preview_only: no
projects: []
---

I think my work colleagues and friends are now bored of me raving about the book Antifragile by Nassim Taleb. My reading style is to read very slowly, mulling over each sentence again and again. When a book is this dense I also tend to make notes. Here they are below, from the point of view of a consultant and a numerical modeller. Some examples are taken straight out of the book whilst others are ones I have personally encountered that illustrate concepts the book raises.

## Consultants don't come out of this looking good
Back in the mists of time, everyone had skin in the game. In an agrarian economy, if you took a risk planting an unusual crop, or grew lax with the safety of your flock, it was your harvest at risk and only yourself to blame. In the modern world there has been a subtle and almost unnoticed risk transfer, where some jobs tend to be exposed to upside whilst transferring the downside risk to others. The archetype of this antifragility of the individual and fragility to society is a bank executive, where the position can enjoy bonuses right up to the moment their business (which they do not own) defaults and costs tax payers a large amount of money to bail out. It is an agency problem, where the agent (bank executive) has misaligned incentives to that of the principle (the bank).

Other more subtle examples include any advisory service where the payment is not linked to the outcome from implementing the advice; pundits and forecasters whose salaries are not linked to the accuracy of their pronouncements are also in this category. Consultants rarely have skin in the game and also commonly fall into this category. So what, if anything, can we do? We need to remove the agency problem by realigning incentives. Structuring the contract so that payment is conditional or proportional to benefit would encourage analytical consultants like myself to model realistically and build in the ability to measure performance. It would also encourage clients to engage with the modelling work they requested and actually implement it, rather than use it to bamboozle a regulator into granting more funding or jump through a regulatory hoop (another agency problem). "Sticky" solutions like subscription based services also tend to align incentives: if the service it provides is rubbish then a customer can elect to leave the following month.

Do we need to go back to what they did in Roman times to keep engineers and builders honest? Back then, if a house that you built fell down and killed someone then you were executed as punishment. No wonder you see lots of Roman buildings and foundations that have survived to the present day.

There are some roles with more than just skin in the game. Taleb refers to these brave individuals as having _soul_ in the game. These days its easy to wonder, where have all the heroes gone? But examples abound: bearers of unwelcome news (prophets in old times), whistle blowers, investigative journalists, opposition leaders in countries under totalitarian rule, and, especially in times of pandemic, medical staff and care home workers. These are the true key workers.

## Optimisation fragilises
Optimisation makes things fragile. An excellent example in the book is the traffic flow problem. It displays convexity, as adding one more car to the road network produces a negligible addition to the average journey time until you reach a critical point where the marginal cost of journey time from one more car becomes exponential. Think about it, you have often taken twice as long on a car or plane journey but how often have you taken _half_ the time you estimated?

Now let's think about this in terms of investment planning, route planning, or similar optimisation problems. You will generally optimise by reducing a cost function (travel time, risk cost, etc.) subject to constraints (sites you must visit, annual budget, etc.) but what is generally neglected is the sensitivity of these constraints, along with related assumptions, to the cost function. Say an infrastructure planner optimally plans a road network for an expected traffic volume. A plan is found that serves the projected growth in road traffic over the next ten years with the minimum cost. The model sees no benefit in oversizing this project, even though a small additional cost may result in a project that delivers much more capacity. Then 6 six years pass and the traffic growth projection was underestimated and when road works coincide with home games at the sports stadium there is mass congestion. 

Planning in such a lean way may appear optimal but is actually fragile. However, fat in the system can mitigate Black Swans. 

### Options rather than determinism

There is something very deterministic about most kinds of modelling - strategic models even more so. Rarely are options presented; it is the one best way/suite of projects in the portfolio/list of assets to replace over a multi-year period and that is that.

The reason that optimisation fragilises is because the act of removing all fat in the system is the removal of optionality. In the book, debt is seen as the ultimate example of fragilisation because it removes all optionality from you.

Thalesian thinking (in terms of optionality and identifying non-linear effects) as opposed to Aristotelian thinking (in terms of precise risk calculation).

Climate change, modelling approaches, portfolio optimisation

## Via negativa
The "do something" fallacy is the mistaken belief that in the face of a problem the act of doing something/anything is always superior to doing nothing. It is closely related to the agency problem, where the agent (e.g., a doctor) must often be seen to be doing something in order to justify their position as an agent, even if premeditated inaction is in the best interest of the priniciple (e.g., the patient). 

One of the most prominent illustrations of this in my work is in asset management, where the no-investment case is always the most risky, and any intervention (whether refurbishment or replacement) will reduce the risk. In general this is true, but there are nuances to the approach. What about infant mortality of assets where damage has occurred during installation or where there are manufacturing defects? How is this superior to not replacing an asset that has exceeded its expected life but is otherwise operating just fine? What about finger tip maintenance or stress tests that due to operator error actually cause failure? The observer effect is a phenomenon not readily acknowledged in asset maintenance. It is worth remembering that the Chernobyl nuclear power station meltdown of 1986 was caused during a drill to test the preparedness for the reactor being operated outside of its limits.

## Burden of proof of the novel.
Tobacco, thalydomide.

## The curse of size
Planning fallacy and how banks became "too big to fail". Small projects have small errors that come out in the wash.

## Top down versus bottom up
Rationalism, or an analytical approach, versus skeptical empiricism. Which one do we subscribe to for numerical modelling?

### The average versus the dispersion
The average temperature of the grandmother problem. Individual people or things are inherently fragile as the effect of departure from average exposes us to harm. Use transformers as an example: time spent above the rated load causes thermal related degradation and harm, proportional to the amount above the threshold and the duration that this is maintained.