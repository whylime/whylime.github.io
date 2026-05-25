---
title: Privacy and transparency of fitness tracking devices
description: 
date: 2026-05-25
tags: [security, privacy]
draft: false
---

TL;DR: Here's a [transparency reporting tracker](https://emilyaustin.github.io/wearable-tracker/) for 12 health/fitness wearable brands.

## Introduction
I've worn a Garmin GPS device for well over a decade. I've logged thousands of activities–runs, rides, swims (ugh), walks, hikes...you name it. If I've moved, it's probably been logged. It's fascinating to look back at this data periodically to see how my fitness has changed over time, and I love being able to monitor progress toward big goals. 

It's not lost on me that this data sitting on someone else's servers could also easily help one determine my current and past addresses, places I've traveled, and periods of high stress or health issues experienced over the years. You could see my biometric data changing slightly in the early days of pregnancy before I even knew I was pregnant; you could pinpoint the exact _minute_ my son was born. (Yes, I wore my Garmin in the hospital. Yes, I love data. No, I have no shame.) I have many friends entrenched in this ecosystem too, though some have chosen different devices (Coros, Apple Watch, etc.).


## Transparency reports
When I saw [Zack Whittaker's recent report](https://this.weekinsecurity.com/oura-says-it-gets-government-demands-for-user-data-will-it-share-how-many/) on wearable Oura ring's privacy and security issues, I was curious how common these issues are across a sample of beloved fitness wearable devices. This particular article focuses on transparency reporting (or in this case, I suppose, lack of).

[Transparency reports](https://en.wikipedia.org/wiki/Transparency_report) explain how often a company receives government or law enforcement requests for user data, and how many it complies with. While Google has published [transparency reports](https://transparencyreport.google.com/user-data/us-national-security) since 2009, more major tech companies adopted the practice following the [2013 Snowden revelations](https://en.wikipedia.org/wiki/Snowden_disclosures) as a direct response to public pressure. Infrastructure companies like [Cloudflare](https://www.cloudflare.com/transparency/), [GitHub](https://github.blog/tag/github-transparency-report/), and [Reddit](https://redditinc.com/policies/transparency) also adopted the same practice. If you're holding sensitive data and governments can compel you to hand it over, users deserve to know how often that happens.

Knowing that Oura doesn't publish a transparency report and doesn't seem like they're going to, I was curious about other fitness and health wearable companies' practices here.

## Findings
I looked at 12 wearable companies to see whether they publish anything in this realm. I was hoping I'd feel better after a little research. Well, dear reader, I do not. Perhaps unsurprisingly, just the two major tech companies on the manufacturer list (Apple and Google) publish transparency reports. Others do not.

It may be a fair criticism to say that these are more niche players and to expect them to publish transparency reports is asking too much, but (as an example) Garmin [provides solutions](https://www.garmin.com/en-US/forms/govanddefensesales/) for all levels of government. Probably not too much to ask that they publish transparency reporting data.

Perhaps a more fair criticism is to say that there may be other more pressing security concerns with these devices. Remember the [Coros issues from mid-2025](https://infosec.exchange/@mle/114775070265230998), made 10x worse by the company's initial blase response about vulnerability remediation? 

{{< figure src ="/images/wearable-transparency/wearable-tracker.png" >}} 

[Here's a dashboard](https://emilyaustin.github.io/wearable-tracker/) that aggregates what I found looking at each of these companies. I plan to keep it updated monthly, and who knows? Maybe we'll see the needle move at some point in the not too distant future.

