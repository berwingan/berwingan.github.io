---
title: Covering Discs and Orthants 📐
---

In this [[capstone.pdf | research]], we examined two interrelated problems. The first problem was to determine the minimum number of unit discs required to cover points in a streaming setting. Specifically, given a stream of points on a plane, we aimed to develop an algorithm that would cover all points with unit discs without storing every point. The second problem we investigated was covering with orthants. In this scenario, there are points on a plane with priorities and every time a new orthant is added, the two points with the highest priorities covered by the orthant will form a connection. The main question was whether or not these orthants could be used to form cliques of arbitrarily large size.

Despite numerous attempts, we were unable to move the upper and lower bounds for the unit disc covering variation. The unique aspect of discs, having only one edge, makes constructing algorithms that compress information difficult to find. One way to understand the difference between discs and other shapes, such as squares or rectangles, is to view it through its dual problem. By keeping the intersections of streamed discs, we are essentially keeping a linear amount of information. This is not the case when streaming squares.

Our results were focused on the various variations of the problem, such as the lower bound for the square variation, a 2-approximation algorithm for the half-space variation for a hitting set of size 1, and a 1.5-approximation algorithm for the interval covering variation with a covering set of size 2.

For the orthant problem, we first showed that using a single type of orthant for construction is equivalent to a planar graph. We then provided a universal construction for the uniform single connection problem, showing that uniform single connections of any size are possible. Finally, we aimed to demonstrate that cliques of arbitrarily large size cannot be constructed using orthants by showing that restricting the construction to 0 and 1 intermediary points makes the construction impossible.

Feel free to explore the whiteboard used [[Capstone_Napkin.pdf|here]].


## Related Papers
1) [Interval selection in the streaming model by Sergio Cabello and Pablo Pérez-Lantero](https://arxiv.org/abs/1501.02285)
2) [Approximation schemes for covering and packing problems in image processing and VLSI by Dorit S. Hochbaum and Wolfgang Maass](https://dl.acm.org/doi/10.1145/2455.214106)
3) [Approximation schemes for covering and packing in the streaming model by Christopher Liaw, Paul Liu, and Robert Reiss](https://arxiv.org/abs/1706.09533)
4) [Improved Results on Geometric Hitting Set Problems by Nabil H Mustafa and Saurabh Ray](https://link.springer.com/article/10.1007/s00454-010-9285-9)
5) [Packing and covering with non-piercing regions by Aniket Basu Roy, Sathish Govindarajan, Rajiv Raman, and Saurabh Ray](https://link.springer.com/article/10.1007/s00454-018-9983-2)


