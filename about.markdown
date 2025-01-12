---
layout: page
title: About
permalink: /about/
---

Hello and welcome! I use this website to organize and record things I've learned, both for myself and for others. Here's a bit about me:

I graduated from Phillips Exeter Academy and later from Brown University with a degree in Applied Mathematics - Computer Science. Afterward, I matriculated into Columbia Medical School. However, after one semester, I realized that medicine was not my calling. Just a month later, I accepted a position at Google.

Now, I am a Senior Software/Reliability Engineer at Google, specializing in high-throughput, distributed, low-latency systems. In simpler terms, the systems I manage process tens of millions of requests daily. The underlying data amounts to exabytes, and response times are measured in milliseconds. Here are some examples of the projects I have worked on:

- **Decreasing data lookup latency** by optimizing the database metadata client cache.
- **Migrating the primary server** from an asynchronous model to a thread-per-request threading model, improving code readability and maintainability.
- **Implementing a user-data privacy layer** and creating a flexible query API over database indexes to ensure compliant data access.
- **Regionalizing user data** both at-rest and in-flight:
  - Splitting the production environment into two shards for better scalability.
  - Auditing requests to ensure compliance with regulatory standards.
  - Auditing data location to maintain compliance with data sovereignty laws.
- **Enhancing a user-data placement pipeline** to reduce read/write latency while ensuring regulatory compliance for data location.
- **Adjusting the load-balancing algorithm** in batch servers to gracefully handle spillover loads while maintaining the latency service level objective (SLO).

I love what I do because it involves solving complex and nuanced problems. My goal is to make these technical concepts as accessible as possible for a wide audience. I hope this site serves as a helpful resource for anyone interested in these topics.
