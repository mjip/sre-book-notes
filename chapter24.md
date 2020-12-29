---
title: "Chapter 24- Distributed Periodic Scheduling with Cron"
authors: ["Stepan Davidovic"]
---

* cron is usually implemented using a single component, which is commonly referred to as crond (a daemon that loads the list of scheduled cron jobs)

* the only state that needs to persist across crond restarts (including machine reboots) is the crontab configuration itself

* independent processes running in the same datacenter should not negatively impact each other

* small writes on a distributed filesystem are very expensive and come with high latency, because the filesystem is not optimized for these types of writes

* Paxos can be used to ensure replicas of the cron service have a consistent state

* the distributed cron uses a single leader job, which is the only replica that can modify the shared state, as well as the only replica that can launch cron jobs (the Fast Paxos leader replica also acts as the cron service leader)

* if the leader replica dies, the Paxos group can elect a new leader. the fast reaction time for the leader re-election stays well within a generally tolerable one-minute failover time

* the follower replicas keep track of the state of the world, as provided by the leader, in order to take over if needed

* crontab plugin- the question mark, meaning any value is acceptable, and the cron system is given the freedom to choose the value

