---
title: "Introduction"
authors: ["Benjamin Treynor Sloss"]
---

* over time, SREs should end up with very little operational load and almost entirely engage in development tasks, because the service basically runs and repairs itself. systems should be *automatic* not just *automated*

* devops emerged in the industry in late 2008, core principles- involvement of the IT function in each phase of a system's design and development, heavy reliance on automation versus human effort, application of engineering practices and tools to operations tasks

* SRE team is responsible for the *availability*, *latency*, *performance*, *efficiency*, *change management*, *monitoring*, *emergency response*, and *capacity planning* of their services

* blame-free postmortem culture: goal of exposing faults and applying engineering to fix these faults rather than avoiding or minimizing them

* an error budget dictates the space left over once the business/product establishes the system's availability budget (e.g. phased rollouts, 1% experiments)

* error budgets resolves the structural conflict of incentives between development and SRE- SRE's goal is no longer zero outages, SRE and product developers aim to spend the error budget getting maximum feature velocity

* monitoring is one of the primary means by which service owners keep track of a system's health and availability

* monitoring should never require a human to interpret any part of the alerting domain- software should do the interpreting, humans should be notified only when they need to take action

* three kinds of valid monitoring output- *alerts*, *tickets*, *logging*

* *alerts*- signify a human needs to take action immediately in response to something that is either happening or about to happen

* *tickets*- signify a human needs to take action, but not immediately

* *logging*- recorded for diagnostic or forensic purposes

* reliability is a function of mean time to failure (MTTF) and mean time to repair (MTTR), the most relevant metric in evaluating the effectiveness of emergency response is how quickly the response team can bring the system back to health (MTTR)

* effective change management- implementing progressive rollouts, quickly and accurately detecting problems, and rolling back changes safely when problems arise

* capacity planning should take into account both organic growth (nartural product adoption and usage) and inorganic growth (feature launches, marketing campaigns)

* provisioning combines both change management and capacity planning

