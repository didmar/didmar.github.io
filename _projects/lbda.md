---
layout: page
title: Data Analytics Platform for marketing
description:
img: assets/img/lbda.png
importance: 3
category: work
---

Stack: [Scala](https://scala-lang.org/), [Spark](https://spark.apache.org/), [Cassandra](https://cassandra.apache.org/_/index.html), [Play Framework](https://www.playframework.com/)

As part of Heuritech's founding team, I was the lead dev on a Data Analytics Platform project for Mediaprism, a marketing agency within the French Post group.

They had access to **connection logs from +700 top French websites** thanks to partnerships, but faced the challenge of how to them effectively: how to extract meaningful data on a user's interests, using nothing but their navigation history?

Fortunately, at Heuritech we had already built a tool to tackle this problem: a **semantic analysis engine**. Leveraging a cutting-edge natural language processing (NLP) technique known as [Word2Vec](https://en.wikipedia.org/wiki/Word2vec), the engine could categorize any web page into a theme (e.g., automobile, politics, gossip...). Rather than a simple rule-based engine (e.g., matching a pre-defined list of words), the engine would compute a semantic proximity with the provided theme, which proved to be much more flexible and works across multiple language without extra work!

```
www.nrj.fr/actu/633-rihanna.html -> music
www.geny.com/arrivee/prix-dione  -> horse riding
...
```

Having a cool NLP tool is nice but... being able to use it on huge amounts of data is another challenge: **200M new events/day** and a **+18B history**.
We selected Apache Spark and Cassandra as the most suitable solution for processing and storing the data, and created a multi-stage pipeline that can be summarized like so:

- Process the raw logs with our NLP tool and store it into a table indexed by user id and timestamp
- Compute aggregates over daily and lifetime activity of each user
- Merge these aggregates over multiple user ids that are actually the same person, as identified by an email address, and integrate CRM data
- Create segments of users that have a sustained interest in a given topic, for the marketing to target them with the right offer at the right timing

The mission took about 9 months, after which I trained the client's technical team to maintain the platform and make it evolve.
It was a great success and enabled us to invest into image analysis and build the [data pipeline](/projects/hcore) used today in Heuritech's products.

# Challenges

The project was extremely ambitious for a few reasons.

Big Data was only starting to be a thing, and when we decided to build our solution on Spark it was still in beta and only available in Scala!
Fortunately, I had already been working with Scala for more than a year, and my good understanding of functional programming made it easy for me to reason with Spark's [Resilient Distributed Datasets](https://spark.apache.org/docs/latest/rdd-programming-guide.html#resilient-distributed-datasets-rdds).
Conceiving the whole pipeline's architecture was still challenging, as it was the first time I had to deal with such a complex data flow.

Another challenge was turning the very recent Word2Vec NLP technique into a production-ready tool. Deep Learning was still a very new field back then, and we had to experiment a lot with our own tooling (also in Scala). I dealt with the integration of the model into the pipeline, and well as with additional tools for the client to be able to configure everything, and occasionally bypassing the model with some manual rules.

We were very fortunate to be given the opportunity to work on such a big project, and I think we honored it by delivering a very solid solution.