---
layout: post
title:  "What is the cloud?"
date:   2025-01-12 10:59:45 -0500
categories: cloud 
---

These days, mentions of the cloud are inescapable. Businesses are often advised to move their digital infrastructure to major cloud providers like [AWS](https://aws.amazon.com/), [GCP](https://cloud.google.com/), and [Azure](https://azure.microsoft.com/). The cloud's success is reflected in the [$626b market size](https://www.gartner.com/en/newsroom/press-releases/2024-05-20-gartner-forecasts-worldwide-public-cloud-end-user-spending-to-surpass-675-billion-in-2024) in 2024. The compound annual growth rate (CAGR) is [predicted](https://finance.yahoo.com/news/cloud-computing-market-worth-usd-130600292.html) to be 18%, translating to a $2.5t market size by 2032. Many [benefits](https://docs.aws.amazon.com/whitepapers/latest/aws-overview/six-advantages-of-cloud-computing.html) are touted: flexibility, scalability, cost savings, increased security, and data loss prevention. However, to the average person, the *cloud* is an abstract concept. Contrary to the name's implication, the computers are not floating around in the sky. Let's explore what the cloud really is.

## Before you walk, you must crawl

When the internet was first created, hosting a website required an individual to buy a server themselves. They'd wait for it to be delivered, plug it into an outlet, install the operating system, install the software needed to run the website, and finally connect it to the internet. In simple terms, when a client typed a website, like `somewebsite.com`, into their browser, their computer sent a request. This request traveled through a series of intermediary computers (routers) to reach the server hosting the website, which was sitting in the individual's house.

However, this setup put the server in a vulnerable position. Here are just a few potential issues:

1. **A power outage:** The outlet stops working, and the server shuts down.
2. **An irrecoverable error in the server:** The website becomes inaccessible.
3. **A house fire:** The server is destroyed.
4. **A thief breaks in:** The server is stolen.
5. **Overheating:** The server melts down due to failed air conditioning.

In all these cases, the website goes offline, causing stress and operational risks for the individual. For example, Facebook’s first servers were [hosted in Mark Zuckerberg’s dorm room](https://www.datacenterknowledge.com/hyperscalers/the-facebook-data-center-faq). This wasn’t that long ago in the grand scheme of things.

## Not my house

"Enough!" they say. "My house floods too often."

The next step in the evolution of hosting was to store the server in a rented space inside a data center managed by someone else. A **data center** is a secure facility designed to house servers with reliable electricity, cooling, and internet connections. This setup reduces operational headaches. The individual is still responsible for buying, installing, and managing their equipment, but if they need to physically restart the server, they can call an on-call worker at the data center.

While this setup addresses many risks, it has one major limitation: it cannot handle spikes in demand. For example, Best Buy’s website experiences a surge of activity on Black Friday. If the servers cannot handle the load, the website crashes. To prevent this, the individual must order more servers ahead of time. However, what happens to these extra servers during the rest of the year? They sit idle, resulting in wasted resources. The issue is that the individual can **only** use servers they own.

## Sharing is caring

The solution to managing demand spikes while avoiding underutilized resources is **resource sharing**. Instead of owning their own servers, the individual rents time and capacity on servers managed by a third party. During peak demand, they can rent more servers. During quieter periods, they can scale down their usage.

For example, imagine a data center containing 100 servers that host 10 websites. In the past, each website might use 10 servers, meaning no flexibility to handle demand spikes. If a website needed 15 servers, it would crash. With the resource-sharing model, all 10 websites can draw from the pool of 100 servers. As long as the total demand doesn’t exceed the available capacity, websites can dynamically adjust their resource use. The larger the pool of resources, the less likely any individual website will face shortages.

## Welcome to the cloud

The sharing model described above is the foundation of what people call the **cloud**. At its core, the cloud is about aggregating compute resources—grouping together the processing power of many servers—and dynamically allocating them to users as needed. This allows companies to rent server time and capacity rather than owning and managing physical equipment themselves.

Cloud providers operate massive data centers around the world, enabling companies to scale their websites globally. For example, if a business experiences increased traffic in Europe, it can deploy resources closer to European users, reducing latency and improving the user experience. This flexibility also adds redundancy—if one data center experiences an issue or even burns down, the cloud provider’s network can ensure the website remains operational by shifting traffic to another location.

In short, the cloud makes it possible for businesses to handle unpredictable demand, reduce operational risks, and optimize costs by paying only for what they use. It’s not magic, but it’s a powerful tool for the digital age.
