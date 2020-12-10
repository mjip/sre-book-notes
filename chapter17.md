---
title: "Chapter 17- Testing for Reliability"
authors: ["Alex Perry and Max Luebbe"]
---

* the mean time to repair (MTTR) measures how long it takes the operations team to fix the bug, either through a rollback or another action

* the more bugs you can find with zero MTTR (caught through tests and prevented from deploying to prod), the higher the mean time between failures (MTBF) is

* software tests broadly fall into two categories- traditional and production. traditional- evaluates correctness of software offline (during development). production- performed on a live web service to evaluate deployed software is working correctly

* *unit tests* are the smallest/simplest form of software testing. they assess a separate unit of software (e.g. a class/function), for correctness independent of the larger software system that contains the unit. unit tests are common for TTD

* *integration tests* are run on an assembled component to verify that it functions correctly. dependency injection and mocks are used to imitate complex dependencies so that an engineer can cleanly test a component (e.g. mock a database)

* *system tests* are the largest scale tests you can run for an undeployed system. all modules belonging to a specific component, such as a server, are assembled into the system. they test end-to-end functionality and come in many different flavours-
	* *smoke tests*- test very simple but critical behaviour, serves to short-circuit additional and more expensive testing (also known as *sanity testing*)
	* *performance tests*- after smoke tests, a common next step is to check the performance of the system stays acceptable over the duration of its lifecycle
	* *regression tests*- system test that prevents bugs from sneaking back into the codebase, collects a gallery of rogue bugs

* *stress tests*- used to find the limits on a web service

* *canary tests*- a subset of servers used to test a new version or configuration before the rest of the release progresses (a.k.a. 'baking the binary')

* if every task is high-priority, none of the tasks are high priority

