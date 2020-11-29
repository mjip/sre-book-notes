---
title: "Chapter 3 - Embracing Risk"
authors: ["Marc Alvidrez"]
---

* extreme reliability comes at a cost - maximizing stability limits how fast new features can be developed and how quickly products can be delivered to users

* *opportunity cost* - the cost borne by an organization when it allocates engineering resources to build systems or features that diminish risk instead of features that are directly visible to or usable by end users

* in a typical application not all requests are created equal

* factors to consider when assessing risk tolerance of servers- 
	* what level of availability is required 
	* do different types of failures have different effects on the service
	* how can we use the service cost to help locate a service on the risk continuum
	* what other service metrics are important to take into account

* which is worse for a service- a constant low rate of failures, or an occasional full-site outage?

* canarying- test a new release on some small susbet of a typical workload

* *SLO* - *service level objective*

* error budgets align incentives and emphasizes joint ownership between SRE and product development, it makes it easier to decide the rate of releases and to effectively defuse discussions about outages with stakeholders, and allows multiple teams to reach the same conclusion about production risk

