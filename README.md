# Network Analysis Tutorial: Centrality Measures & Community Detection

A hands-on Jupyter notebook tutorial that introduces two core topics of network analysis: **centrality measures** (which nodes are important?) and **community detection** (which groups of nodes belong together?).

Each technique comes with its intuition, its mathematical definition, the original reference, and annotated Python code that explains what every function does and how it works internally.

## Learning objectives

After working through the notebook, you should be able to:

1. Explain *why* we measure centrality and *why* we look for communities in networks.
2. Describe the intuition, mathematics, and original references behind the most widely used centrality measures and community detection algorithms.
3. Compute each measure and algorithm in Python with `networkx`, understand the role of each function argument, and interpret the output.
4. Compare methods against each other and against a known ground truth.

## Dataset

The tutorial mainly uses **Zachary's Karate Club** (Zachary, 1977), a social network of 34 club members and 78 friendships. During the study, a conflict split the club into two factions. Because this real split is known, you can check how well each algorithm recovers it. The dataset is built into `networkx`, so no download is needed.

## Contents

### Part 0: Setup and graph refresher
Basic graph concepts (nodes, edges, adjacency matrix, degree, shortest paths), loading and visualizing the dataset, and helper functions for plotting.

### Part 1: Centrality measures

| Measure | Idea | Key reference |
|---|---|---|
| Degree | Number of direct ties | Freeman (1978) |
| Closeness | Inverse of the mean distance to all other nodes | Bavelas (1950); Sabidussi (1966) |
| Betweenness | Share of shortest paths passing through a node | Freeman (1977); Brandes (2001) |
| Eigenvector | Being connected to other important nodes | Bonacich (1972, 1987) |
| PageRank | Random surfer with teleportation | Brin & Page (1998) |

Also included: from-scratch calculations checked against `networkx` (closeness, power iteration for eigenvector centrality), plus a comparison section with side-by-side plots, the nodes the measures disagree about most, and a Spearman correlation heatmap.

### Part 2: Community detection

| Algorithm | Approach | Key reference |
|---|---|---|
| Modularity (quality function) | Observed vs. expected within-community edges | Newman & Girvan (2004) |
| Greedy modularity (CNM) | Agglomerative modularity maximization | Clauset, Newman & Moore (2004) |
| Louvain | Multi-level modularity optimization | Blondel et al. (2008) |
| Leiden | Louvain plus a refinement step that guarantees connected communities | Traag, Waltman & van Eck (2019) |
| Label propagation | Nodes adopt their neighbours' most common label | Raghavan, Albert & Kumara (2007) |

Also included: a plain-language explanation of NMI and ARI with a small worked example, the effect of the resolution parameter and random seed, a side-by-side comparison of all partitions, and a section linking centrality to community structure through node roles (Guimerà & Amaral, 2005).

### Part 3: Summary, exercises, and references
Summary tables, four exercises for you, and a full reference list.

## Getting started

### Run locally

```bash
git clone https://github.com/kadircihanduran/SoDA-502-Analytical-Tutorial.git
cd REPO
pip install -r requirements.txt
jupyter notebook network_analysis_tutorial.ipynb
```

## Requirements

- Python 3.9 or newer
- `networkx` 3.x
- `numpy`, `scipy`, `pandas`, `matplotlib`, `scikit-learn`
- `jupyter`
- *Optional:* `python-igraph` and `leidenalg` for the Leiden section. If they are not installed, that cell prints an install hint and is skipped, and the rest of the notebook runs normally.

The notebook was tested with networkx 3.6, scikit-learn 1.8 and pandas 3.0.

## Repository structure

```
.
├── network_analysis_tutorial.ipynb   # The tutorial notebook (saved with outputs)
├── requirements.txt                  # Python dependencies
└── README.md                         # This file
```

## Main references

- Fortunato, S. (2010). Community detection in graphs. *Physics Reports*, 486(3–5), 75–174.
- Freeman, L. C. (1978). Centrality in social networks: Conceptual clarification. *Social Networks*, 1(3), 215–239.
- Hagberg, A. A., Schult, D. A., & Swart, P. J. (2008). Exploring network structure, dynamics, and function using NetworkX. *Proceedings of the 7th Python in Science Conference*, 11–15.
- Newman, M. E. J. (2018). *Networks* (2nd ed.). Oxford University Press.
- Zachary, W. W. (1977). An information flow model for conflict and fission in small groups. *Journal of Anthropological Research*, 33(4), 452–473.

The complete reference list is in Part 3 of the notebook.
