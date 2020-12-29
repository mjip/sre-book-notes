---
title: "Chapter 27- Reliable Product Launches at Scale"
authors: ["Rhandeev Singh","Sebastian Kirsch","Vivek Rau"]
---

* launch coordination engineers specialize in guiding developers toward building reliable and fast products that meet standards for robustness, scalability, and reliability

* developing a launch checklist, consider:
	* architecture and dependencies- if the service is using shared infra correctly
	* integration- if the new product integrates well into the internal ecosystem (e.g. setting up new machines, configuring new services, monitoring, load balancing, DNS)
	* capacity planning- traffic peak at launch, redundancy, availability, extra datacenter/network resources
	* failure modes- identify the impact of failure for each component/dependency
	* client behaviour- protecting against abusive user behaviour, web scrapers, DOS attacks
	* processes/automation- all newly introduced processes are documented
	* development process- most development is on the mainline branch, but releases are built on separate branches per release
	* external dependencies- code library maintained by third parties, service/data provided by another company. these risks can be mitigated by filtering/rewriting proxies, data transcoding pipelines, caches
	* rollout planning- enabling individual features for different subsystems

* first stages of a rollout are called canaries, meant to detect dangerous effects from the behaviour of the new software under real user traffic

* feature flag frameworks- meant for small changes, potentially tested in the hundreds in parallel, early prototypes for select users

* simplest feature flag framework for user interface changes- HTTP payload rewriter at frontend application servers, limited to a subset of cookies or another similar HTTP request/response attribute (e.g. cookie hash mod range, whitelists/blacklists)

