---
title: "Chapter 20- Load Balancing in the Datacenter"
authors: ["Alejandro Forero Cuervo"]
---

* backend tasks- services composed of 100-1000 processes

* client tasks- hold connections to the backend tasks, for each incoming query a client task must decide which backend task should handle the query

* in an ideal case, the load for a given service is spread perfectly over all its backend tasks and the least and most loaded backend tasks consume exactly the same amount of CPU

* flow control- when the active request count reaches a configured limit, the client treats the backend as unhealthy and no longer sends it requests

* lame duck state- the backend task is listening on its port and can serve, but is explicitly asking clients to stop sending requests

* advantages- simplifies clean shutdown, avoids serving errors to all unlucky requests that happened to be active on backend tasks that are shutting down

* subsetting- limiting the pool of potential backend tasks with which a client task interacts

* use a larger subset size if the number of clients is significantly smaller than the number of backends, or there are frequent load imbalances within the client jobs (i.e. one client task sends more requests than others)

* naive implementation of subset selection- each client randomly shuffles the list of backends once and fills its subset by selecting resolvable/healthy backends from the list

* deterministic subsetting- divides client tasks into rounds, within each round, each backend is assigned to exactly one client

* load-balancing policies- mechanisms used by client tasks to select which backend task in its subset receives a client request. examples- round robin, least-loaded round robin, weighted round robin

* weighted round robin incorporates backend information into the decision process. each client task keeps a capability score for each backend in its subset. requests are distributed in round-robin fashion, but clients weight the distributions of requests to backends proportionally. in each response, backends include the current observed rates of queries and errors/sec, in addition to utilization (e.g. CPU usage). clients adjust capability scores periodically to pick backend tasks based upon their current number of successful requests handled and at what utilization cost; failed requests result in a pnealty that affects future decisions

