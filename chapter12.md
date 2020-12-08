---
title: "Chapter 12- Effective Troubleshooting"
authors: ["Chris Jones"]
---

* "being an expert is more than undertanding how a system is supposed to work. expertise is gained by investigating why a system doesn't work"

* troubleshooting depends on two factors- an understanding of how to troubleshoot generically and a solid knowledge of the system

* troubleshooting is an application of the hypothetico-deductive method- given a set of observations about a system and a theoretical basis for understanding system behaviour, we iteratively hypothesize potential causes for the failure and try to test those hypotheses

* you can test your hypothesis in 2 ways- comparing the observed state of the system against the theory to find confirming or disconfirming evidence, or actively changing the system in a controlled way and observing the results

* common pitfalls-
	* looking at symptoms that aren't relevant or misunderstanding system metrics (wild goose chase)
	* misunderstanding how to change the system, its inputs, or its environment
	* coming up with wildly improbable theories about what's wrong
	* latching on to causes of past problems and wrongly assuming that since it happened once, it must be happening again
	* hunting down correlations that are actually coincidences or correlated with shared causes

* not all failures are equally probable- "when you hear hoofbeats, think of horses not zebras"

* first course of action after triage should be to *stop the bleeding*, you aren't helping your users if you're root-causing

* in a multilayer system where work happens throughout a stack of components, it's often best to start systematically from one end of the stack and work toward the other end, examining each component in turn. in larger systems, you can *bisect* the system and examine communication paths between components on one side and the other

* a malfunctioning system is often still trying to do something- just not the thing you want it to be doing. finding out *what* it's doing, then asking *why* it's doing that and *where* its resources are being used or where its output is going can help you understand how things have gone wrong

