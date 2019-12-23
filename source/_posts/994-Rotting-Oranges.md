---
title: 994-Rotting-Oranges
date: 2019-08-21 17:18:03
tags: BFS
---

This problem is actually very similar to the **1162. As far from land as possible**. Rotten orange is the land cell, fresh orange is the water cell, and the number of minutes to found is the distance between a rotten orange and a fresh orange.

For each fresh orange, we want to find the minimum of its distance to a rotten orange. Then find the maximum for all fresh oranges.