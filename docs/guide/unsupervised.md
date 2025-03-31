---
layout: home
title: "Unsupervised mode"
parent: User Guide
# has_children: true
# permalink: docs/guide/unsupervised
nav_order: 3
---

# Unsupervised mode

---

With unsupervised mode, each sample will be regarded as one group.

```yaml
python /path_to_metilene3/metilene3.py [-i <string>] [-o <string>] [optional options...]
```

## Parameters:

(Go to [DMR calling](./DMR.html) and [DMTree](./DMTree.html) for more details!)

| parameter | unit  | default | description
|:--------|:-------------------------------|:---|:------------------------------|
| -i, \--input | string |  | the input methylation data, [format](../quick-example.html#cpg-methylation-matrix-methylationmat)
| -o, \--output | string |  | the output directory
| -t, \--threads | integer | 1 | _(optional)_ number of threads
| -s, \--seed | integer | 1 | _(optional)_ set seed for random generator
| -O, \--outputImputed | bool | False | _(optional)_ True or False, save the CpG methylation matrix with imputed values as file ```imputed.tsv```
| -p, \--verbose | bool | False | _(optional)_ True or False, track the process
| -M, \--maxdist | integer | 300 | _(optional)_ maximum distance between two CpG, [details](./DMR.html#presegmentation)
| -m, \--minCpGs | integer | 10 | _(optional)_ minimum CpGs, [details](./DMR.html#segmentation)
| -d, \--minMethDiff | double | 0.1 | _(optional)_ minimum mean methylation difference, [details](./DMR.html#segmentation)
| -r, \--minDMR | integer | 5 | _(optional)_ minimum CpGs with minimum mean methylation difference in a segment, [details](./DMR.html#segmentation)
| -v, \--valley | double | 0.7 | _(optional)_ a cutoff for the difference between global and regional methylation differences, [details](http://legacy.bioinf.uni-leipzig.de/Software/metilene/Manual/#parameter_-v)
| -D, \--minMethDiffHigh | double | 0.5 | _(optional)_ minimum mean methylation difference for DMTree and GSEA, similar to ```-d, --minMethDiff``` but a higher value will be recommanded to reduce the number of false positive DMRs, [details](./DMR.html#segmentation)
| -u, \--clusteringRatio | double | 0.5 | _(optional)_ maximum ratio of CpGs with minimum difference in a cluster, [details](./DMR.html#clustering)
| -n, \--minNSamples | integer | 3 | _(optional)_ minimum samples in a cluster, [details](./DMTree.html)
| -w, \--minSumDMRs | integer | 100 | _(optional)_ minimum sum of DMR weights to split samples, [details](./DMTree.html)
| -plot, \--visualization | bool | False | _(optional)_ plot PCA and heatmap based on DMR methylation
| -anno, \--annotation | string |  | _(optional)_ hg19 or hg38, use ChIPseeker to annotate the DMRs 
| -refs, \--refSeq | string |  | _(optional)_ reference genome, ```fasta``` file, for sequence annotation
| -gsea, \--genesets | string |  | _(optional)_ geneset ```gmt``` file for GSEA
| -wsup, \--withSupervised | bool | True | _(optional)_ run supervised mode after clustering

