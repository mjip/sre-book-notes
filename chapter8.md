---
title: "Chapter 8 - Release Engineering"
authors: ["Dinah McNutt"]
---

* release engineering works in collaboration with software engineers in product development and SREs to define all the steps required to release software- from how the software is stored in the source code repo to build rules for compliation to how testing/packaging/deployment are conducted

* self-service model- in order to work at scale, teams must be self-sufficient

* high velocity- user-facing software is rebuilt frequently, frequent release == fewer changes between versions

* push on green release model- deploy every build that passes all tests

* hermetic builds- insensitive to the libraries/other software installed on the build machine. if two people attempt to build the same product at the same revision number in the source code repo on different machines, the build executables should be identical

* gated operations for releases-
	* approving source code changes
	* specifying the actions to be performed during the release process
	* creating a new release
	* approving the initial integration proposal
	* deploying the new release
	* making changes to a project's build configuration

* branching strategy- releases branched off of mainline at a specific revision, hotfixes merged into mainline and cherry picked into release branch (release branch never gets merged back)

