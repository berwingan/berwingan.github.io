---
layout: post
title: "Fixing Anchor Protocol Incentives"
author: "Berwin Gan "
categories: research
tags: [research]
image: ../capstone_photos/first.png
---

I am glad to announce the submission of my capstone in computational geometry with Professor Saurabh Ray titled "Approximations for Covering in a Streaming Setting, Covering with Orthants"

We looked primarily at two different but related problems. The first was the question of finding the minimum number of unit discs to cover points in a streaming setting, that is, given a bunch of streaming points onto a plane, how can we create an algorithm that will cover all points with unit discs without storing every point. We then investigated covering with orthants. The enviroment was that there are points on a plane with priorities and everytime we add a new orthant, the two points with the two highest priorities covered by the orthant will form a connection. The big question was whether or not we could use these orthants to form cliques of arbitrarily large size.

For our first problem, we did not move the upper and lower bounds for the unit disc covering variation despite numerous attempts. For the upper bound, it seems that it is the unique fact that discs only have one edge that makes constructing algorithms that compresses information hard to find. One way we can easily see how disc differ from other shapes such as square or rectangles is to view it through its dual problem. By keeping the intersections of streamed discs, we are essentially keeping a linear amount of information. This is not the case if we were instead to streamed squares. 

Our results were instead on the various variations such as the lower bound for the square variation, a 2-approximation algorithm for the half-space variation for a hitting set of size 1 and a 1.5-approximation algorithm for the interval covering variation with a covering set of size 2.

For the orthant problem, we first showed that using a single type of orthant for the construction is equal to a planar graph. After that, we give a universal construction for the  uniform single connection problem showing that uniform single connections of any size is possible. Lastly, we worked towards showing that cliques of arbitrarily large size cannot be constructed using orthants by showing that restricting the construction to 0 and 1 intermediary points makes the construction impossible.

If you are interested, please read the paper [here](/assets/pdf/capstone.pdf)
