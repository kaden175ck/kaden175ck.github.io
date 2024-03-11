---
layout: post
title: "Null Model"
date: 2024-02-27
categories: SNA
permalink: "/SNA/NullModel"
---
**What is a Null Model?**

A null model is like a "fake" spider web you make to compare to the real one.  Here's why that's cool:

* **Understanding Special Patterns:**  Say you notice a cluster of friends who all like the same video game. Is that just random, or is there something special causing that cluster? A null model helps! You make a fake friend group with the same number of people, randomly connected. If this "fake" web doesn't usually have clusters of gamers, that means your real-life network's pattern is probably not random, and something interesting is going on!
* **Focusing on Important Features:**  Maybe you care how easily info spreads in a network. You make a null model keeping the same number of nodes and connections, but the links are all shuffled up. This tells you what kind of spread to normally expect, letting you see if your real network is better or worse at spreading info.

**Simple Example**

1. **Your Real Network:** A map of your neighborhood, showing who's friends with who.
2. **A Null Model:** Same number of houses, but friendships are assigned randomly.
3. **Comparison:** Maybe your real neighborhood has lots of friend groups, but the random one doesn't. That means something is likely causing friend clusters to form in your actual neighborhood!

**Key Points**

* Null models are like a "what-if" experiment with networks. 
* They help you tell if what you see in a real network is special or just expected by chance.
* It's all about comparing the real network to a randomized version of itself.


**A Deeper Dive**
* **Types of Null Models:**

    1. **Configuration Model:**  Preserves the degree of each node (number of connections it has). This is helpful for studying features like clustering or path lengths while controlling for the overall level of connectivity.
       ![Alt text for the image](/assets/images/configmodel1.png)

        * Null model is created by repeatedly swapping edges while keeping the degrees the same.

        ![Alt text for the image](/assets/images/configmodel2.png)

    2. **Erdős-Rényi Model:**  The simplest kind.  You focus on the number of nodes and edges, assuming each edge exists with a fixed probability. This is like the "completely random spider web".
       ![Alt text for the image](/assets/images/ermodel1.png)

        * Null model is a completely random graph with the same number of nodes and edges.

        ![Alt text for the image](/assets/images/ermodel2.png)

    3. **Other specialized models:**  Can get very specific. Some models preserve spatial constraints (for geographical networks), directedness (important for networks where the flow of information matters), or even weights on the edges.






