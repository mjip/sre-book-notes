---
title: "Chapter 21- Handling Overload"
authors: ["Alejandro Forero Cuervo"]
---

* when overloaded- redirect when possible, serve degraded results when necessary, and handle resource errors transparently when all else fails

* modeling capacity as 'queries per second' or using static features of the requests often makes for a poor metric/moving target for designing/implementing load balancing

* CPU consumption as the signal for provisioning works well- in platforms with garbage collection, memory pressure naturally translates to increased CPU consumption, and in other platforms, it's possible to provision the remaining resources in such a way that they're unlikely to run out before CPU runs out

* define per-customer limits based on CPU allocation

* when a customer is out of quota, a backend task should reject requests quickly with the expectation that returning a 'customer is out of quota' error consumes significantly fewer resources than actually processing the request/serving back a correct response

* adaptive throttling- each client task keeps the last two minutes of its history- requests at the application layer, and accepts by the backend. once requests is 2x the number of accepts, the client will begin to self-regulate and new requests are rejected locally

* criticality- associated values for priority of request- CRITICAL_PLUS, reserved for the most critical requests that result in user-visible impact if they fail; CRITICAL- default value for requests sent from production jobs, less severe; SHEDDABLE_PLUS- traffic for which partial unavailbility is expected (default for batch jobs which can retry requests later); and SHEDDABLE- traffic for which frequent partial unavailbility and occasional full unavailability is expected

* the criticality of a request is orthogonal to its latency requirements and underlying network quality of service (QoS)

