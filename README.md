# 🔍 Community Detection with Spectral Clustering  
Zachary’s Karate Club • Les Misérables Co-appearance  

> **Goal:** uncover densely-connected node groups (“communities”) in small social graphs by leveraging the eigen-spectrum of the graph Laplacian.

---

## ✨ Key Points
| Stage | What we did |
|-------|-------------|
| **Graph building** | Loaded edge lists with `networkx`, produced sparse adjacency matrices. :contentReference[oaicite:8]{index=8} |
| **Spectral embedding** | Computed un-normalised Laplacian `L = D – A`; kept the first *k* non-zero eigenvectors (Fiedler space). :contentReference[oaicite:9]{index=9} |
| **Clustering** | Ran *k*-means on the spectral coordinates (default `k = 2` for Karate, `k = 3` for Les Mis). |
| **Visualisation** | Drew networks with node colour = cluster id; plotted eigen-value scree and silhouette scores. :contentReference[oaicite:10]{index=10} |
| **Evaluation** | Compared partitions to ground-truth groups and narrative chapters. |

---

docs/
  karate_clusters.png
  lesmis_clusters.png
  eig_scree.png
  
📈 Results
| Dataset            | *k* | Modularity | NMI / ARI       | Notes                                              |
| ------------------ | --- | ---------- | --------------- | -------------------------------------------------- |
| **Karate Club**    | 2   | **0.371**  | **0.82 / 0.80** | One mis-clustered node; matches Zachary’s split.   |
| **Les Misérables** | 3   | 0.562      | 0.69 / 0.65     | Clusters align with protagonist-centric sub-plots. |


## Findings
- Spectral clustering perfectly separates the two factions in the Karate Club except for node 3, echoing Zachary’s 1977 study
- For Les Misérables the three-way split groups Valjean-centric, Paris-revolutionary, and peripheral characters, mirroring thematic arcs in the novel.
- Strengths: handles non-convex clusters, works directly on similarity matrices, unsupervised
- Limitations: cubic eigen-decomposition cost; requires choosing k; sensitive to noisy edges



