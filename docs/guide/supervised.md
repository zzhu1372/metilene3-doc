---
layout: home
title: "Supervised mode"
parent: User Guide
# has_children: true
# permalink: docs/guide/supervised
nav_order: 4
---

# Supervised mode

---

With supervised mode.

```yaml
python /path_to_metilene3/metilene3.py [-i <string>] [-g <string>] [-o <string>] [optional options...]
```

## Parameters:

(Go to [DMR calling](./DMR.html) for more details!)

| parameter | unit  | default | description
|:--------|:-------------------------------|:---|:------------------------------|
| -i, \--input | string |  | the input methylation data, [format](../quick-example.html#cpg-methylation-matrix-methylationmat)
| -g, \--groupinfo | string |  | the input group information table, [format](../quick-example.html#group-information-table-samples_groupstsv)
| -o, \--output | string |  | the output directory
| -t, \--threads | integer | 1 | _(optional)_ number of threads
| -s, \--seed | integer | 1 | _(optional)_ set seed for random generator
| -O, \--outputImputed | bool | False | _(optional)_ True or False, save the CpG methylation matrix with imputed values as file ```imputed.tsv```
| -p, \--verbose | bool | False | _(optional)_ True or False, track the process
| -M, \--maxdist | integer | 300 | _(optional)_ maximum distance between two CpG, [details](DMR.html#presegmentation)
| -m, \--minCpGs | integer | 10 | _(optional)_ minimum CpGs, [details](DMR.html#segmentation)
| -d, \--minMethDiff | double | 0.1 | _(optional)_ minimum mean methylation difference, [details](DMR.html#segmentation)
| -D, \--minMethDiffHigh | double | 0.5 | _(optional)_ minimum mean methylation difference for GSEA, similar to ```-d, --minMethDiff``` but a higher value will be recommanded to reduce the number of false positive DMRs, [details](./DMR.html#segmentation)
| -r, \--minDMR | integer | 5 | _(optional)_ minimum CpGs with minimum mean methylation difference in a segment, [details](DMR.html#segmentation)
| -v, \--valley | double | 0.7 | _(optional)_ a cutoff for the difference between global and regional methylation differences, [details](http://legacy.bioinf.uni-leipzig.de/Software/metilene/Manual/#parameter_-v)
| -anno, \--annotation | string |  | _(optional)_ hg19 or hg38, use ChIPseeker to annotate the DMRs 
| -refs, \--refSeq | string |  | _(optional)_ reference genome, ```fasta``` file, for sequence annotation
| -gsea, \--genesets | string |  | _(optional)_ geneset ```gmt``` file for GSEA