---
title: "Chapter 23- Managing Critical State: Distributed Consensus for Reliability"
authors: ["Laura Nolan"]
---

* the CAP theorem holds that a distributed system cannot simultaneously have all three of the following properties- consistent views of the data at each node, availability of the data at each node, and tolerance to network partitions

* e.g. if two nodes can't communicate (because the network is partitioned), then the system as a whole can either stop serving some or all requests at some of all nodes (reducing availability), or it can serve requests as usual, but result in inconsistent views of the data at each node

* traditional ACID datastore semantics (atomicity, consistency, isolation, durability), more modern BASE (basically available, soft state, eventual consistency). BASE advantages- can handle large volumes of data and transactions that would be more costly/infeasible than ACID

* eventual consistency- writes can be committed to different processes concurrently, and there is some mechanism to resolve conflicts (e.g. last timestamp wins)- multimaster replication

* if a file server cannot contact its partner, it issues a STONITH (shoot the other node in the head) command to its parter node to shut the node down, then take mastership of its files

* Byzantine failures occur when a process passes incorrect messages due to a bug or malicious activity

* FLP impossibility result- no asynchronous distributed consensus algorithm can guarantee progress in the presence of an unreliable network

* solutions to distributed consensus problem- Lamport's Paxos protocol, Raft, Zab, Mencius

* Paxos- in the first phase, the proposer sends a sequence number to the acceptors. each acceptor will agree only if it has not yet seen a propozal with a higher sequence number. proposers can try again witha higher sequence number if necessary (must be unique, drawing from disjoint sets or incorporating their hostname into their number). if a proposer receives agreement from a majority of acceptors, it can commit the propozal by sending a commit msg with a value. this means- two different values cannot be committed for the same proposal (because any two majorities will overlap in at least one node), and acceptors must write a journal on persistent storage whenever they agree to accept a proposal, because the acceptors need to honour these guarantees after retarting

* zookeeper, consul, etc, chubby use consensus algorithms as clients of some service that implement these algorithms

* replicated state machine (RSM)- a system that executes the same set of operations, in the same order, on several processes. you can use a sliding-window protocol to reconcile state between peer processes in an RSM

* replicated services use a single leader to perform some specific type of work in the system; the single leader mechanism is a way of ensuring mutual exclusion at a coarse level

* barrier- a primitive that blocks a group of processes from proceeding until some condition is met (e.g. until all parts of one phase of a computation are completed)

* locks- a coordination primitive that can be implemented as an RSM (e.g. prevents multiple workers from processing the same input file). in practice use renewable leases with timeouts- locks can be held indefinitely by processes that crash

* system should ensure claimed tasks from a queue are successfully processed (use a lease system). queues implemented as an RSM prevent blocking the whole system from operating should the queue be lost

* atomic broadcast- primitive in which messages are received reliably and in the same order by all participants

* queuing-as-work-distribution pattern- uses the queue as a load balancing device, point-to-point messaging

* multi-Paxos protocol- uses a strong leader process; unless a leader has not yet been elected or some failure occurs, it requires only one round trip from the proposer to a quorum of acceptors to reach consensus

* dueling proposers is a form of livelock (proposals repeatedly interrupt each other and no proposals can be accepted)

* scaling read workload is critical because many workloads are read-heavy

* quorum leases- aimed at reducing latency and increasing throughput for read operations. performing a strongly consistent read requires either a distributed consensus operation that reads from a quorum of replicas, or a stable leader replica that is guaranteed to have seen all recent state changing operations. useful for read-heavy workloads concentrated in a single geographic region

* consensus systems constraints on performance of committing state changes- network RRT and time to write data to persistent storage

* fast Paxos- meant to improve its performance over wide area networks, clients send propose messages directly to each member of a group of acceptors instead of through a leader. if the client in the fast Paxos system has a high RTT to the acceptors, and the acceptors have fast connections to each other, fast Paxos can be slower than classic Paxos

* due to the latency tail effect, a single round trip across a slow link with a distribution of latencies is faster than a quorum

