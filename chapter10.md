---
title: "Chapter 10- Practical Alerting"
authors: ["Jamie Wilkinson"]
---

* monitoring enables service owners to make rational decisions about the impact of changes to the service, apply the scientific method to incident reponse, and measure the sevice's alignment with business goals

* riemann, heka, bosun, prometheus

* borgman stores all data in an in-memory database, regularly checkpointed to disk. the data points have the form (timestamp, value) and are stored in chronological lists called time-series, and each time-series is named by a unique set of labels of the form name=value

