---
layout: post
title: equals() vs ==
date: 2025-09-01 16:00:00 +/-1000
categories: [Learning, Data Structure]
tags: [data_structure, red_black_tree]     # TAG names should always be lowercase
author: mayRhee
---
## Rule

In red-black tree, there are **4** rules.

1. Every node is either red or black.

2. Root and every leaf(Null pointer) are black

3. If a node is red, both children are black.

4. Every path from node to descendent leaf contains the same number of black nodes


## Insertion

new node should be red.