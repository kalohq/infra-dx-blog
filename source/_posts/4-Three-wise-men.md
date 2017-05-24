---
title: 4. Three wise men
date: 2017-05-24 23:22:15
---

> This is a sprintly summary of upcoming, delivered and in-progress work for the **Infra DX Crew**.
> It'll contain technical musings, <SOMETHING ELSE> and probably a few memes.
>
> #### TLDR
> 
> - We have a new crew member! Welcome **Alex Pate**!
> - We're taking a week off! (Not quite so bluntly but we do have a few holidays over this sprint and the next)
> - We rebranded! Huge effort from Yannis and AP on planning and executing the engineering side.
> - There's an awesome new "Skeleton UI Kit" coming
> - Work is ticking along nicely on the performance focus
>   - Core bundles are at >30% reduction
>   - Done an initial investigation into data loading (work being scoped)
>   - Kicking off scoping of work around ux patterns
> - Not too much in **Release Watch** this week. Most releases take an hour from prep to deploy.

## _"What even is Myrrh?"_

We have added a seriously wise man to the crew in AP. With our focus being on ensuring engineers have what they need to deliver a good platform while also keeping that platform working as smooth as possible we saw a definite alignment with Alex's goals. Alex focus is, with a design mindset, to bring stability and consistency to how we engineer UI's at Lystable. At least that's what it is until he tells me that's wrong after he reads this. Anyhow!

Get on with it, Chris.

## What we worked on

Where has our focus been?

#### Smoothest Rebrand EVER

Thanks to some awesome planning and work by Yannis, AP and the rest of the rebrand team this execution on Monday went off and was completed within under 2 hours.

<br/>
![smooooth](https://media.giphy.com/media/AP94i0chEPXSU/giphy.gif)
<center>Smoother than P Diddy</center>
<br/>

It's worth noting that there is still lots of internal infra that will be renamed over coming weeks so keep your eye out for "Lystable", whatever *that* is.

#### Performance investigation

We've spent some time investigating the loading performance of certain areas of our application and by breaking down events into a high level timeline we've been able to target some improvements to make.

See the initial glimpse [here](https://github.com/kalohq/frontend/blob/10015a8ca2d3a43ca5a40fb6b60ff4fc18a16377/docs/research/170516-data-fetching-performance.md)

Here's an example timeline we came up with:

```
-----> | Fetch unrelated queries for hidden ui
-----> | Fetch projects list
       | ---> | void (cpu churn?)
              | -----> | Fetch related freelancers
              | -----> | Fetch related users
                | ---> | void (cpu churn?)
                       | -----> | Fetch freelancer & user image files
                       | -----> | Fetch freelancer skills (unused)
                       | -----> | Fetch freelancer profiles (unused)
                                | ---> | void (cpu churn?) before rendering results
```

We'll be taking this and discussing across cohorts what actions we can take to fix the issues here. We'll aim to scope up this work so we can prioritise it this quarter.

#### Skeleton layouts

In an effort to make loading of pages less janky we are introducing a design paradigm called "skeleton loading". This shows rough outlines of the anticipated content layout while it is loading. We can show this while loading assets, data or anything!

You can follow the PR for this ui kit [here](https://github.com/kalohq/ui/pull/7).

![skeleton ui](https://cloud.githubusercontent.com/assets/1042432/26374037/c222cfa4-3ffb-11e7-9589-65a686083db9.png)

## Release Watch

Going to ignore the hotfixes for the rebrand here since they are very special cases. (v0.199.1 f/e, v0.214.1 b/e)

#### Frontend

- 1 minor release (70 mins)
- 2 hotfix releases (1 hour and 5.5 hours)

#### Backend

- 1 minor release (72 mins)

#### Takeaways

- We're generally sitting around an hour for releases which which is pretty good but we hope to improve!
- Should investigate why a hotfix was sitting around for nearly 6 hours

## What's up next?

What's the plan, batman?

##### Holiday Season

Yannis is only here one day next week (in the sprint) where he'll be mostly tidying up final rebrand infra bits and doing a bit of work on slow category updates.

I (Chris) am only here Thursday/Friday and I'm focusing on getting the code splitting work into a "ready to merge and release" state while scoping a ton of work for next month across design, frontend and backend (all focused around performance).

##### Continued marketing migration

AP is continuing to migrate old marketing pages into the new site.

You can see all the planned work for this sprint on our [jira board](https://lystable.atlassian.net/secure/RapidBoard.jspa?rapidView=13)!

> Thanks for reading!
> Chris