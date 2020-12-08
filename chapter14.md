---
title: "Chapter 14- Managing Incidents"
authors: ["Andrew Stribblehill"]
---

* a well-designed incident management process has the following features- 
	* recursive separation of responsibilities- everyone involved in the incident should have a role and doesn't stray onto someone else's turf
	* several distinct roles should be delegated to particular people-
		* incident command- holds the high-level state about the incident, structures incident response task force, can remove roadblocks
		* operational lead- works with the incident commander to respond to the incident by applying operational tools to the task at hand (they should be the only person modifying the system during an incident)
		* communication- public face of the task force, issues periodic updates to the incident response team/stakeholders, may keep incident document up-to-date and accurate.
		* planning- deals with longer-term issues, like filing bugs, arranging handoffs, and tracking how the system has diverged from the norm so it can be reverted once the incident is resolved

* in some incidents, locating the task force members into a central 'war room' is appropriate to troubleshoot

* set clear conditions for declaring an incident- do you need to involve a second team in fixing the problem? is the outage visible to customers? is the issue unsolved even after an hour's concentrated analysis?

* prioritize- stop bleeding, restore service, preserve evidence for root-causing

* prepare- develop/document your incident management procedures in advance, consult with incident participants

* trust- give full autonomy within the assigned role to all incident participants

* introspect- pay attention to your own state, solicit more support if needed

* consider alternatives- periodically consider your options and re-evaluate whether it still makes sense to continue or if you should take another track

* practice- use the process routinely so it becomes second nature

* change it around- swap roles with each incident and encourage team members to acquire familiarity with each role
