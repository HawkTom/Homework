### AAI-Homework

---

**1. Perform a hierarchical clustering of the one-dimensional set of points 1, 4, 9, 16, 25, 36, 49, 64, 81, assuming clusters are represented by their centroid (average), and at each step the clusters with the closest centroids are merged.**



![图片1](..\img\hw_USL.png)

<br>

**2.  For the three clusters in the figure:**

- **(a) Compute the representatives of the cluster as in the BFR Algorithm. That is, compute N, SUM, and SUMSQ.**
- **(b) Compute the variance and standard deviation of each cluster in each of the two dimensions.**

![图片1](..\img\hw_USL1.png)

*Sol:* 

(a).

|         |  Cluster 1  | Cluster 2  |  Cluster 3  |
| :-----: | :---------: | :--------: | :---------: |
|   $N$   |      4      |     3      |      5      |
|  $SUM$  | $(21, 36)$  | $(10, 8)$  | $(54, 21)$  |
| $SUMSQ$ | $(117,328)$ | $(38, 24)$ | $(590, 95)$ |

(b). 

|                        |   Cluster 1   |   Cluster 2    |    Cluster 3    |
| :--------------------: | :-----------: | :------------: | :-------------: |
|      **Variance**      | $(1.6875, 1)$ | $(1.56, 0.89)$ | $(1.36, 1.36)$  |
| **Standard deviation** |  $(1.30, 1)$  | $(1.25,0.94)$  | $(1.166,1.166)$ |

