---
title: "Chapter 25- Data Processing Pipelines"
authors: ["Dan Dennison"]
---

* data pipeline design pattern- reads in data, transforms it in some desired way, outputs new data (e.g. co-routins, DTSS communication files, the Unix pipe, ETL pipelines)

* multiphase piplines- programs typically organized into a chained series, with the output of one program becoming the input to the next (designed for ease of reasoning about the system and not usually geared towards operational efficiency). depth- number of programs chained together

* periodic pipelines are generally stable when there are sufficient workers for the volume of data and execution demand is within computational capacity (this becomes fraile whenever organic growth and change inevitably begin to stress the system)

* hanging chunk problem- resources are assigned due to differences between machines in a cluster or overallocation to a job

* Moire load pattern- occurs when two or more pipelines run simultaneously and their execution sequences occasionally overlap, causing them to simultaneously consume a common shared resource

* MVC for data pipelines- model- task master, holds all job states in memory for fast availability. view- workers that continually update the system state transactionally with the master. workers can be stateless if master only stores pointers to input/output data in common filesystem. controller- supports number of auxilliary system activites that affect the pipeline, e.g. runtime scaling, snapshotting, workcycle state control, rolling back pipeline state

* workflow correctness guarantees-
	* worker output through configuration tasks creates barriers on which to predicate work
	* all work committed requires a currently valid lease held by the worker
	* output files are uniquely named by the workers
	* client and server validate the task master itself by checking a server token on every operation

