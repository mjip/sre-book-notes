---
title: "Chapter 19- Load Balancing at the Frontend"
authors: ["Piotr Lewandowski"]
---

* traffic is distributed across multiple network links, datacenters, and machines in an optimal way

* latency is measured in round-trip time (RTT)

* layers of load balancing- DNS, VIPs

* DNS middleman- recursive resolution of IP addresses, nondeterministic reply paths, additional caching complications

* recursive resolvers typically cache responses and forward those responses within limits indicated by the TTL field in the DNS record

* RFC 1035- all DNS replies served should fit within the 512-byte limit, this bounds the number of addresses that can be contained in a single DNS reply

* virtual IP addresses are not assigned to any particular network interface, they're usually shared across many devices

* VIP implementation- network load balancer: receives packets and forwards them to one of the machines behind the VIP

* several approaches- least loaded backend, but not optimal in the case of stateful protocols (which must use the same backend for the duration of a request)

* consistent hashing- describes a way to provide a mapping algorithm that remains relatively stable even when new backends are added/removed from the list

* direct server response (DSR) provides a ton of savings if user requests are small and replies are large, since only a small fraction of traffic would need to traverse the load balancer

* packet encapsulation- a network load balancer puts the forwarded packet into another IP packet with generic routing encapsulation (GRE) and uses the backend's address as the destination. a backend receiving the packet strips off the outer IP+GRE layer and processes the inner IP packet as if it were directly delivered to its network interface. as long as the route between the network load balancer and the backend exists, they can be in separate broadcast domains

* disadvantages of PE- inflated packet size (24 bytes in the case of IPv4+GRE), which can cause packets to exceed the maximum transmission unit (MTU) and require fragmentation, but if the MTU is configured to be larger within the datacenter, the network needs to support large protocol data units

