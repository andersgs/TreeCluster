# ClusterPicker-II
ClusterPicker-II is a tool that, given a tree *T* (Newick format) and a distance threshold *t*, finds the minimum number of clusters of the leaves of *T* such that some user-specific constraint is met in each cluster. The user can also specify a branch support threshold *s* such that no pair of leaves in any cluster can be connected by branches with support below *s*. The default method is "Max Clade" (see [Clustering Methods](#clustering-methods)).

ClusterPicker-II was motivated by [ClusterPicker](https://github.com/emmahodcroft/cluster-picker-and-cluster-matcher).

## Usage
```bash
usage: ClusterPickerII.py [-h] [-i INPUT] -t THRESHOLD [-s SUPPORT]
                          [-m METHOD]

optional arguments:
  -h, --help            show this help message and exit
  -i INPUT, --input INPUT
                        Input Tree File (default: stdin)
  -t THRESHOLD, --threshold THRESHOLD
                        Length Threshold (default: None)
  -s SUPPORT, --support SUPPORT
                        Branch Support Threshold (default: -inf)
  -m METHOD, --method METHOD
                        Clustering Method (options: max, max_clade) (default:
                        max_clade)
```

## Clustering Methods
* **Max Clade:** Cluster the leaves such that the following conditions hold for each cluster:
    1. The maximum pairwise distance between leaves in the cluster is below *t*
    2. Leaves cannot be connected by branches with support below *s*
    3. The leaves in the cluster must define a clade in *T*

* **Max:** Cluster the leaves such that the following conditions hold for each cluster:
    1. The maximum pairwise distance between leaves in the cluster is below *t*
    2. Leaves cannot be connected by branches with support below *s*

## Requirements
* [Biopython](http://biopython.org/)
