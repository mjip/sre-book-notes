---
title: "Chapter 26- Data Integrity: What You Read Is What You Wrote"
authors: ["Raymond Blum","Rhandeev Singh"]
---

* data integrity is a measure of the accessibility and accuracy of the datastores needed to provide users with an adequate level of service, and that services in the cloud remain accessible to users/user access to data is especially important, so this access should remain in perfect shape

* maintaining data integrity- proactive detection and rapid repair/recovery

* uptime- also referred to as availability, the proportion of time a service is usable by its users

* latency- how responsive a service appears to its users

* scale- a service's volume of users and the mixture of workloads the service can handle before latency suffers or the service falls apart

* velocity- how fast a service can innovate to provide users with superior value at reasonable cost

* BASE allows for higher availability than ACID in exchange for a softer distributed consistency guarantee (BASE only guarantees that once a piece of data is no longer updated, its value will eventually become consistent across storage locations)

* no one really wants to make backups, what people really want are restores

* backups can be loaded back into an application while archives cannot

* archives safekeep data for long periods of time to meet auditing, discovery, and compliance needs

* an effective restore plan must account for any of these failure modes occurring in any combination. factors of data integrity failure modes:
	* root cause- an unrecoverable loss of data may be caused by any number of factors; user action, operator error, application bugs, defects in infra, fauly hardware, site catastrophes
	* scope- losses can be widespread or narrow/directed
	* rate- data losses can be a one-time event or creeping 

* layers of defense against data loss-
	* soft/lazy deletion- deleted data is marked, rendering it unusable except through admin code paths, but destroyed after a reasonable delay (e.g. 15-60 days). lazy deletion- data that is deleted by a cloud application becomes immediately inaccessible to the application, but is preserved by the cloud service provider for a few weeks
	* backups/data recovery
	* replication- every storage instance, including backup instances, would be replicated

* in theory, Paxos ignores failed compute nodes and can make progress as long as a quorum of functioning nodes is maintained. in practice, ignoring a failed node may correspond to timeouts, retries, and other failure-handling approaches beneath the particular Paxos implementation

* out-of-band data validation is useful to detect creeping data loss- only validate invariants that cause devastation to users

