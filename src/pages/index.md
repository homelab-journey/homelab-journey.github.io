---
title: Getting started
pageTitle: Homelab Journey - Just one way to homelab.
description: Just documenting my way through setting up a homelab to learn, have fun, and make something.
---

This is just one way to set up a homelab. I am documenting my way through setting up my homelab. You are welcome to come along for the journey and you are encouraged to deviate the "plan" for whatever works for you! {% .lead %}

{% quick-links %}

{% quick-link title="Architecture Guide" icon="presets" href="/docs/concept-architecture" description="A living set of documents and diagrams to give a 50,000ft view of the plan." /%}

{% quick-link title="Automation" icon="plugins" href="/docs/concept-automation" description="Let's remove the \"human element\" and have a machine do the work!" /%}

{% quick-link title="Hardware" icon="installation" href="/docs/concept-hardware" description="Step-by-step guides to setting up your system and installing the library." /%}

{% quick-link title="My Apps" icon="theming" href="/docs/my-apps" description="Learn to easily customize and modify your app's visual design to fit your brand." /%}

{% /quick-links %}

Possimus saepe veritatis sint nobis et quam eos. Architecto consequatur odit perferendis fuga eveniet possimus rerum cumque. Ea deleniti voluptatum deserunt voluptatibus ut non iste.

---

## How to use this documentation

This documentation is intended for my homelab and yours will surely be different. However many of the concepts can be carried over. A lot of what I put her will be intended for me. So there may be a callout that is meant to jog my memory but I will attempt to make them verbose enough to make sense.

### A few callouts

Code blocks for doing the things will be denoted by a block like we see below

```shell
npm install typescript -g
```

If there is something in this documentation that could result in a bad day if its not done correctly, it will show up like so!

{% callout type="warning" title="Oh no! Something bad happened!" %}
This is what a disclaimer message looks like. You might want to include inline `code` in it. Or maybe you’ll want to include a [link](/) in it. I don’t think we should get too carried away with other scenarios like lists or tables — that would be silly.
{% /callout %}

{% callout title="Now you Know!" %}
This is what a disclaimer message looks like. You might want to include inline `code` in it. Or maybe you’ll want to include a [link](/) in it. I don’t think we should get too carried away with other scenarios like lists or tables — that would be silly.
{% /callout %}

---

## Homelabbing

Homelabbing is great but there are a couple of things to think about.

### 1. Finacials

It is easy to look at some of these homelabs and be a little envious. Or maybe be discouraged because you don't have the same gear. I want to tell you not to fret, don't feel discouraged, and don't chase after more than you can afford. While you can have a huge homelab with tens-of-thousands of dollars worth of gear.

It doesn't take much to get started. A Raspberry Pi, an old laptop or thin client. I started with a couple Raspberry Pi and saved up here an there while watching eBay and Facebook Market place to find deals that I could upgrade to.

### 2. Utility

Another thing to consider is the cost of run a homelab. In some places especially in Europe the cost of utilities has gone up astronomically. Be lofty when peicing together your homelab and be forward-thinking when it comes to overall-performance, performance-per-watt, and needs. Maybe you don't need frequency, you need core count. Trade-offs can be beneficial and something to keep in mind when trying to "right-size" a solution that fits your needs.

### 3. But... Cloud First?

I get it, as a Solutions Architect focused on the AWS space, I find it hard to not default to a cloud native environment. However, part of the appeal for me when homelabbing is that my homelab works for my home, even when the network is down. I do believe there is a place for "the cloud" in the home though. My philosophy has been cloud-second. Where possible I have things running locally and backing up to the cloud. e.g. a NAS that backs up to S3 in the cloud. "If you only have one, you have none".

---

## Getting help

I don't have all the answers &amp; I when I do have an answer it may not always be the best answer. However, I will always help however I can. Together we can find the person to persons that may know what we need.

### Join the community

I don't know that I want to create yet-another-discord for yet another homelaber. Maybe we can start a giant discord server for multiple homelabers? Maybe we can even get the grand masters to join in ([@technotim](https://twitter.com/TechnoTimLive), [@raidowl](https://twitter.com/RaidOwlTweets), [@craftcomputers](https://twitter.com/CraftComputing), [@christianlempa](https://twitter.com/ChristianLempa))
