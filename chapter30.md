---
title: "Chapter 30- Embedding an SRE to Recover from Operational Overload"
authors: ["Randall Bosetti"]
---

* more tickets should not require more SREs- the goal of the SRE model is to only introduce more humans as more complexity is added to the system

* ops mode- certain method of keeping a service running (e.g. having a greater number of admins managing newly spun up VMs for a service). SRE focuses on writing software or eliminating scalability concerns so that the number of people required to run a service doesn't increase as a function of load on the service

* identify kindling (emergencies waiting to happen)-
	* knowledge gaps
	* services deployed by SRE that are quietly increasing in importance
	* strong dependence on the next big thing- people might ignore problems for months because they believe the new solution that's on the horizon obviates temporary fixes
	* common alerts that aren't diagnosed by either the dev team or SREs- frequently triaged as transient (investigate alerts fully or fix the alerting rules)
	* any service that is both the subject of complaints from your clients and lacks a formal SLI/SLO/SLA
	* any service with a capacity plan that is effectively 'add more servers'- capacity plans should be forward-looking
	* postmortems that only have action items for rolling back the specific changes that caused an outage
	* any serving-critical component for which the existing SREs respond to questions by saying 'the devs own it'

* bad apple theory- the system is working fine, and if we get rid of all the bad apples and their mistakes, the system will continue to be fine (false)- mistakes are inevitable in any system with multiple subtle interactions

* focus on creating (or restoring) the right initial conditions and teaching the small set of principles needed to make healthy choices

* an SLO is probably the single most important lever for moving a team from reactive ops work to a healthy, long-term SRE focus

