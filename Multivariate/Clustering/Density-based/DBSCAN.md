# DBSCAN
A density-based clustering algorithm that produces a partitional and partial clustering, in which the number of clusters is automatically determined by the algorithm.

- Core points  
  There points are in the interior of a density-based cluster. A point is a core point if there are at least $MinPts$ within a distance of $Eps$, where $MinPts$ and $Eps$ are user-specified parameters.
- Border points  
  A border point is not a core point, but falls within the neighborhood of a core point.
- Noise points  
  A noise point is any point that is neither a core point nor a border point.

## DBSCAN algorithm
1. Label all points as core, border, or noise points.
2. Eliminate noise points.
3. Put an edge between all core points within a distance $Eps$ of each other.
4. Make each group of connected core points into a separate cluster.
5. Assign each border point to one of the clusters of its associated core points.