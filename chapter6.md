---
title: "Chapter 6 - Monitoring Distributed Systems"
authors: ["Rob Ewaschuk"]
---

* *monitoring* - collecting, processing, aggregating, and displaying real-time quantitative data about a system, such as query counts/types, error counts/types, processing times, and server lifetimes

* *white-box monitoring* - monitoring based on metrics exposed by the internals of the system, including logs, interfaces like the JVM profiling interface, or an HTTP handler that emits internal stats

* *black-box monitoring* - testing externally visible behaviour as a user would see it

* *dashboard* - an application that provides a summary view of a service's core metrics. may contain filters, selectors, etc

* *alert* - a notification intended to be read by a human. can be classified further as tickets, email alerts, and pages

* *root cause* - a defect that, if repaired, instills confidence that this event won't happen again in the same way

* motivations to monitor- analyzing long term trends, comparing over time/experiment groups, alerting, building dashboards, conducting ad hoc retrospective analysis/debugging

* four golden signals of monitoring- latency, traffic, errors, and saturation

* *saturation* - how full your service is, shows constrained resources

* *choose an appropriate resolution for measurements* - observing CPU load over a minute could hide tail latencies, but polling a service too often might be unnecessarily frequent

* "As simple as possible, no simpler"

* like all software systems, monitoring can become so complex that it's fragile, complicated to change, and a maintenance burden

