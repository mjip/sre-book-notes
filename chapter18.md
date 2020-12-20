---
title: "Chapter 18- Software Engineering in SRE"
authors: ["Dave Helstroom, Trisha Weir, Evan Leonard, Kurt Delimon"]
---

* SREs can design/create software with the appropriate considerations for dimensions such as scalability, graceful degradation during failure, and the ability to easily interface with other infrastructure or tools

* guiding principle- "team size should not scale directly with service growth"

* traditional capacity planning- collect demand forecasts, devise build and allocation plans, review and sign off on plan, deploy and configure resources. this is a never-ending cycle- assumptions change, deployments slip, budgets are cut

* capacity request from a service is generally an inflexible set of demand requirements- X cores in cluster Y (bin-packing in an NP-hard problem)

* solution- intent-based capacity planning. specify the requirements, not the implementation. programmatically encode the dependencies and parameters (intent) of a service's needs, and use that encoding to autogenerate an allocation plan that details which resources go to which service in which cluster.

* *intent* is the rationale for how a service owner wants to run their service

* *performance data* describes how a service scales- for every unit of demand *X* in cluster *Y* how many units of dependency *Z* are used (units can be load, past performance, etc)

* *per-service demand forecast data* describes the usage trend for forecasted demand signals (e.g. forecasted queries/s by continent)

* *resource supply* provides data about the availability of base-level, fundamental resources 

* *resource pricing* provides data about how much base-level, fundamental resources cost. the prices inform the overall calculated costs, which act as the objective to minimize

* *intent config* defines what consititutes a service and how services relate to one another

* software egnosticism- writing the software to be generalized to allow myriad data sources as input
