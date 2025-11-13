# DSC212_Karate_Club_Assignment
# Community Detection in Zachary's Karate Club Network Using Spectral Modularity
---
#### ASIF ALI M A
#### IMS24050
---
# Recursive Modularity-Based Community Detection in Zachary's Karate Club Network

##  Project Overview
This project applies **recursive spectral modularity bisection** to detect communities in the famous **Zachary's Karate Club** social network dataset.  
The goal is to identify distinct subgroups in the network by repeatedly splitting it using the **leading eigenvector** of the modularity matrix, until no further modularity improvement is possible.

The implementation includes:
- Modularity matrix computation  
- Eigen-decomposition for community splitting  
- Recursive partitioning  
- Centrality metric tracking (degree, betweenness, closeness, clustering)  
- Visualization of each iteration and metric evolution  

---

##  Tasks Completed
- Implemented modularity-based spectral bisection algorithm  
- Added recursive splitting until modularity could not be increased  
- Visualized community formation at each iteration  
- Computed and plotted node-level centrality metrics across iterations  
- Highlighted key leaders (Node 0: *Mr. Hi*, Node 33: *Officer*)  
- Summarized final community structure and metrics  

---

##  Algorithm Used: Recursive Spectral Modularity Bisection

The algorithm uses the **modularity optimization principle** to detect communities.

### Modularity Matrix
$$
B_{ij} = A_{ij} - \frac{k_i k_j}{2m}
$$

Where:

- \(A_{ij}\): adjacency matrix entry (1 if nodes *i* and *j* are connected)
- \(k_i\): degree of node *i*
- \(m\): total number of edges


### Eigenvector-Based Split

Compute the leading eigenpair \((\lambda_1, u_1)\) of the modularity matrix \(B\).

Split nodes based on the sign of \(u_1\):

$$
s_i =
\begin{cases}
+1, & u_{1,i} > 0 \\
-1, & u_{1,i} \le 0
\end{cases}
$$

If \(\lambda_1 > 0\), the split increases modularity and is accepted.

Recurse on each subgraph until all communities are indivisible.

This approach ensures that every partition maximizes modularity locally.


---

##  How the Algorithm Works (Summary)
- The full network starts as one group.  
- The modularity matrix \(B\) is calculated for the current group.  
- The leading eigenvector of \(B\) determines how nodes are split into two subgroups.  
- Each valid split (where λ₁ > 0) is recursively repeated.  
- The process stops when further splitting no longer improves modularity.  
- The result is a hierarchy of stable, high-modularity communities.  

---

##  Results
- The Karate Club network divides into clear communities that match the real-world social split between **Mr. Hi’s group** and **the Officer’s group**.  
- Nodes **0 (Mr. Hi)** and **33 (Officer)** exhibit the highest centrality values, confirming their leadership roles.  
- Metric evolution plots show how node influence stabilizes as modularity converges.  
- The algorithm effectively detects both **major factions** and **smaller intermediate clusters** depending on modularity threshold.

---

##  Metrics Tracked
For each iteration, the following centrality measures were computed:
- **Degree centrality:** node connectivity
- **Betweenness centrality:** node influence on shortest paths
- **Closeness centrality:** node reachability within its subgraph
- **Clustering coefficient:** local group cohesiveness

---

##  Conclusion
The recursive spectral modularity algorithm accurately identified the community structure of the Karate Club network.  
The results align with the known social split, demonstrating the effectiveness of modularity-based spectral methods for detecting communities in real-world networks.  
Tracking node centrality evolution also revealed leadership patterns and the stabilization of structural roles as communities formed.

---

##  Citation
Zachary, W. W. (1977). *An Information Flow Model for Conflict and Fission in Small Groups.*  
Journal of Anthropological Research, 33(4), 452–473.

If you use this implementation or parts of it in academic work, please cite the original paper and mention this repository as a reference implementation of modularity-based community detection.

---

## 🧰 Requirements
To run the notebook:
```bash
pip install numpy networkx matplotlib pandas
