---
layout: post
title: "Understanding Degree Centrality"
date: 2024-02-24
categories: SNA
---

### Degree

Picture a group of friends where each friend is a "node" in a network. The number of friends (or connections) a person has is their "degree." So, someone with a high degree is pretty popular, as they're connected to many others in the group. It's like having a lot of friends on social media.

### Betweenness Centrality

Imagine you're at a party, and there's that one person who introduces friends from different circles to each other. In the network world, we measure how crucial someone (or something, like a bridge) is in connecting different groups with "Betweenness Centrality." If a path or a person has high betweenness, they're like the social butterflies of the network, connecting various clusters.


### Density

Think about a close-knit group where everyone knows each other. This group is "dense" because all possible connections are nearly fulfilled. In contrast, a larger group where people only know a few others isn't as dense. Network density gives us an idea of how interconnected everyone is, on a scale from "everyone's BFFs" to "acquaintances at best."

### Centrality Measures

In any social circle or network, some folks are just more pivotal than others. That's where centrality measures come into play, helping us spot the VIPs of the network. There are a few ways to do this:

- **Degree Centrality**: This one's straightforward. The more connections a node has, the more central it is to the network. It's like being the person who's invited to every party because they know everyone.
  
- **Closeness Centrality**: This tells us how close a node is to all other nodes. High closeness centrality means you can spread news (or gossip) quickly because you're just a few steps away from everyone else.

- **Betweenness Centrality**: It's about being the bridge between different groups. High betweenness means you often find yourself in the role of the connector, making you crucial for the flow of information.
