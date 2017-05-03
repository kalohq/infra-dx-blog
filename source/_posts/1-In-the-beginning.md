---
title: '1. In the beginning'
date: 2017-05-03 21:01:48
---

> This is a sprintly summary of upcoming, delivered and in-progress work for the **Infra DX Crew**.
> It'll contain technical musings, <SOMETHING ELSE> and probably a few memes.

## First post, WOW!

This is the first post of a near infinite series. We were wondering, in the newly founded Infra DX Crew, how we could push our communication up a notch and ensure everyone can keep on top of what we're working on and, perhaps more importantly, *why* we are working on what we are.

On top of the day-to-day communication in Slack we wanted to put together a summary of our sprints where we could keep a nice archive of all our progress and experiences. We wanted this to be a little more engaging and put a personal twist on it so thought a **blog** would be the perfect medium for that! Writing up our experiences on a semi-regular basis should also help us consolidate our direction better.

So I quickly (with a lot of face palming) threw together a blog using [hexo](https://hexo.io) and here we are...

<br/>
<center>**The Infra DX Blog!**</center>

![wow](http://static.tumblr.com/f40cff9477fc5392797426019909d533/wihposx/uUUmspw88/tumblr_static_20130822184519uid2425.jpg)
<center>wow wow wow wow wow</center>
<br/>

This sprint series (1-to-Infinity) will be central to the blog but we'll throw a few more interesting posts in where they may be needed.

Let's go!

## So, what on earth is *Infra DX*?

I'll try to explain this quickly but I'm sure there will be a fuller post coming soon to go into more detail! 

**Infra = Infrastructure**
**DX = Developer Experience**

On one hand we have identified a need to deliver stable and efficient infrastructure to our teams within Lystable. This could be anything from providing an easy-to-use framework for building certain parts of UI to delivering a platform which allows teams to quickly release new features *on their own*.

On the other "Developer Experience" encompasses everything to do with the happiness and efficiently of developers on a day-to-day basis. Ie. Making sure engineer workflows are smooth or that designers and engineers can work together without a fuss.

So as a crew it is our responsibility to push the quality of these experiences and tools. We aren't the only ones though! All crews actively contribute towards these goals - we're just a bit of dedicated focus.

## What we worked on

Where has our focus been?

#### Tracking apis and performance metrics

One of our big focuses as an engineering team in Q2 is on performance around our critical flows. Before you can improve performance however you need to be able to track it. This was essentially our *first big project* together on the Infra DX Crew and I'm quite pleased with the result!

On the one end we have a shiny new [generic tracking service](https://github.com/lystable/tracking) with the awesome [kibana 5](https://www.elastic.co/blog/kibana-5-0-0-released) front-end for building dashboards. On the front-end we now have some [benchmarking utilities](https://github.com/lystable/lystable-frontend/pull/1787) and a basic [tracking api](https://github.com/lystable/lystable-frontend/pull/1806) which acts as an interface to the back-end.

![front-end performance dashboard](./fe-perf.png)

Above you can see one of our new dashboards for monitoring front-end performance. With these we will be able to get solid key metrics to track with the result being to deliver a faster and more responsive experience to our users!

> It's now super easy to start tracking your own metrics (of *any* kind) and build a dashboard. If you want help setting something up give the crew channel a shout on slack!

#### Monitoring portal

With all these new monitoring and tracking services it was beginning to be a bit of a pain to try and remember how to find anything. You're probably even thinking *"where are those shiny performance dashboards you just teased us with?!"*.

Well, we decided to throw together a quick monitoring portal so now there's just one thing to remember! You can find that at [monitoring.lystable.com](monitoring.lystable.com)

![monitoring portal](./monitoring-portal.png)

> This actually sparked a bit more of an idea in my mind that we could have a portal for *all* things. Anyway, another time...

#### Massive CI feedback improvements

*We hit under 30mins on our full front-end builds!!* Is that seriously a 50% improvement?! Releases are also fully done within 10mins! This is the quickest our CI has been since summer last year! I am never going to stop over-using exclaimation marks!!

<br/>
![under 30min builds](./under-30mins.png)
<center>Beautiful.</center>
<br/>

An amazing effort by Yannis on this work. By parallelising our test runs, removing some build redundnacy and mastering Tetris we were able to practically halve our wild build times.

This isn't all. We improved the feedback loop by notifying sooner than Circle on individual step failures. It's common for circle to continue running after a test failure so you don't get any notification until *some time later*. Now we let you know in slack *as soon* as something goes wrong! SWEET.

<br/>
![notifications](./quick-notifications.png)
<center>Always good news first.</center>
<br/>

You can take a look at the work [here](https://github.com/lystable/lystable-frontend/pull/1830) and [here](https://github.com/lystable/lystable-frontend/pull/1779).

> We definitely won't be stopping here forever. When we pick this up in the future the new aim will be for under 15 minutes!

#### DX Survey

Nearly everybody completed the DX @ Lystable survey and the anonymised and shuffled responses are [freely available](https://docs.google.com/spreadsheets/d/1rW13o5kpwmCa33OLiFCregqEzMEFgtI7lbD0wAgnics/edit#gid=0). In coming weeks we'll be drilling down further into some of these topics as a DX focus.

Thanks again to all those who added their thoughtful responses - some really great insights!

#### Crew support

To help keep other crews ticking we've been picking up a few small product improvements or bug fixes here and there to catch some slack. So far so good and it hasn't really affected our sprints too much!

## Some musings

A few bits we've been thinking about.

#### Driving pull requests within crews

One of the things which has been growing as an issue is turnaround time on codereviews. There are many many angles to this but one of them is not really having the *right* people find the time to focus on them.

What we've seen as the beginning of a trend seems to be working really well to solving this problem. That is **identify fellow crew members** to help push work through. This will never be an exclusive thing, especially while we need some more people in the crews and have "cohort work", but a crew should be able to rally together to get work shipped and a big part of that is having the work reviewed! Another great positive of this is that crew members will have the most context on the actual product requirements.

So a) next time you are planning your work, take into account what the crew is planning to ship in a sprint so you can make some time for reviews and b) try nudging your crew before looking beyond. It's likely you'll see a better response that way!

## What's up next?

What's the plan, batman?

#### PaaS: Platform as a service!

![mesos](https://mesosphere.com/wp-content/themes/mesosphere/library/images/views/why-mesos/mesos-logo.png?v1)

Boom! As part of a drive to enable truly autonymous crews who can ship all the time we are looking to deliver a PaaS. This should allow teams to easily create and orchestrate releases of new work with a focus being on the back-end services initially.

In this sprint we are planning to get a PaaS running with the nameko deployment principally flowing through that. After that (next sprint) we'll be looking at tying in nicities such as alerting and logging to this platform. Very much MVP for now!

Check out [INFRA-31](https://lystable.atlassian.net/browse/INFRA-31) to track the work (there's an awesome MVP checklist there).

#### Improved front-end user delivery

On the front-end to reduce the initial time it takes for users to download and start using the application we will be looking at optimising our delivered bundles.

<br/>
![](https://pbs.twimg.com/media/C7JTmf1W4AEJSfI.jpg:large)
<center>Our current bundle looks something like this ^</center>
<br/>

The work here will have two focuses:

1) Reduce parse and initialisation time from a MASSIVE amount of javascript
2) Reduce download overhead of a MASSIVE amount of javascript

There's a few pieces of work to move towards this but the main gist of it is a) only deliver what the user needs for their current view (code splitting) and b) just optimise the hell out of and reduce redundnacy of all the code we ship down the wire.

Check out [INFRA-18](https://lystable.atlassian.net/browse/INFRA-18) to track the work.


## Cya!

Okay time for me to wrap up this post. I'll leave you with Yannis' overight airport sleeping dilemma.


![](./yannis-airport.jpg)
<center><i>"Just not sure if its gonna work with my height"</i></center>
<br/>


> This first post was probably a bit more lengthy than future posts. There's also a distinct lack of memes.
>
> Hope you found it useful still!
> Chris