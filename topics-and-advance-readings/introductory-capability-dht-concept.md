# Introductory Capability DHT

Submission to: Rebooting the Web of Trust #8 (March 2019, Barcelona)
Author: James Foley < james.foley@protonmail.com >

The Object Capability software design paradigm is a powerful philosophy for the programming of decentralized applications particularly in the realms of security and rights management. 

There is great potential natural interoperability between programs through the interfaces of capabilities, easing efforts of program compositionality and enabling social interaction much greater than the sum of its parts. A wide variety of applications are possible and one can imagine fabric allowing applications to travel amongst hosts, remaining virtually accessible regardless of their physical substrate, not to mention the normal model of deploying an application to any server available. Any social application could be built in such a paradigm, be it a personal agent, or an application that is a larger composition of agents in some configuration, for instance a user’s personal application representing their own selves introducing itself to a private social network of peers, a refugee organization aiding their search for sanctuary, or what have you. 

**A key detail of such a system would be addressability for purposes of introduction between agents using durable names to connecting different nodes to create new networks, in a similar way that IP is employed today.**

This may demand a solution that works as an introductory network to a wide array of capability based systems, even ones running on different protocols and contexts, or perhaps even systems that are not compatible. It could work as a public utility providing resilient connectability to any application.

One implementation solution could be a distributed capability routing network comprised of a DHT such that the keys would be resilient permanent addresses at which to reach up-to-date routing information with which to connect to an application at the prevailing moment. The advantages of such an approach would be resilience against centralized authorities with regard to addressing information. A node could migrate hosting infrastructure and its location on the  internet all while maintaining a reliable address in the form of a capability registered on such a DHT and visible and consumable to all.

A user running a node in this capability routing network would participate in the routing requests to their destination addresses. It would also be able to provide routing information at its own address that would be used to render a connection to the capability based application it is concerned with. Such information could simply be IP address and authentication information such as a capability address to invoke at that destination, or the node could be running a program to determine how to most correctly connect the incoming request to its larger application at that prevailing moment. 

A Kademlia style DHT would be a candidate to deploy such a network, mainly with regard to its addressing abilities with its built in notion of distance in address space. It would provide efficient routing towards an introductory capability. Storage optimizations such as caching data throughout the network would likely be meaningless for reasons of security possibly liveness. For security, caching throughout different nodes on the netowkr may invalidate a key affordance of such a network, the network privacy to each application utilizing it. For liveness, it may be potentially difficult to continually update the cached values of a key, which could cause problems for an application of scale trying to introduce new agents.

At the same time, incoming requests would be very light weight and therefore throughput would not necessarily suffer. Should that become a bottleneck, then there is nothing stopping one application from occupying multiple keys on the DHT with introductory capabilities.

This system stands apart from DNS and other decentralized solutions for addressing in the way that it would be a pure capability network, where each capability is granularly published, as opposed to different subdomains holding a single capability, depending on the hosting of that larger domain.

It would lend itself to a pure capability workflow and all the potential tools afforded by that such as formal verification and clear legibility of roles in a distributed context.
