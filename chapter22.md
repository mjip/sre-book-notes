---
title: "Chapter 22- Addressing Cascading Failures"
authors: ["Mike Ulrich"]
---

* majority of cascading failures are caused by server overload, resource exhaustion (CPU- increased number of in-flight responses, excessively long queue lengths, thread starvation, CPU/request starvation, missed RPC deadlines, reduced CPU caching benefits; Memory- dying tasks, increased rate of garbage collection, reduction in cache hit rates; Threads; file descriptors; dependencies among resources, service unavailability)

* load test the server's capacity limits, and test the failure mode for overload, perform capacity planning

* load shedding- dropping some proportion of load by dropping traffic as the server approaches overload conditions, to keep the server from running out of RAM, failing health checks, serving with extremely high latency, or any other symptoms with overload

* deadline propagation- deadline is set high in the stack, tree of RPCs emanating from an initial request will all have the same absolute deadline, subtracting time spent in the current call

* propagating cancellations reduces unneeded or doomed work by advising servers in an RPC call stack that their efforts are no longer necessary

* steps to take to address a cascading failure- increase resources, stop health check failures/deaths, restart servers, drop traffic, enter degraded modes, eliminate batch load, eliminate bad traffic
