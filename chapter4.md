---
title: "Chapter 4 - Service Level Objectives"
authors: ["Chris Jones, John Wilkes, Niall Murphy, Cody Smith"]
---

* metrics defining a level of service- *service level indicators (SLIs)*, *objectives (SLOs)*, and *agreements (SLAs)*

* *indicator* - defined quantitative measure of some aspect of the level of service that is provided e.g. request latency, error rate, system throughput (requests/s), availability/yield, durability

* *obective* - target value or range of values for a service level that is measured by an SLI. SLI <= target / lower\_bound <= SLI <= upper\_bound

* *agreements* - explicit or implicit contract with your users that includes consequences of meeting or missing the SLOs they contain

* service SLIs:
	* user-facing serving systems- availability, latency, throughput
	* storage systems- latency, availability, durability
	* big data systems- throughput, end-to-end latency
	* all systems- correctness

* metrics that are collected once per minute and averaged per second might hide bursts and latency

* most metrics are better thought of as distributions rather than averages- averages can obscure tail latencies (use percentiles for requests/s)

