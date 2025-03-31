---
layout: home
title: "Quick Start"
parent: User Guide
nav_order: 2
---


# Quick Start
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Input file(s)

1. **CpG methylation matrix**: ```methylation.tsv``` <br> This matrix should include chromosome, position and CpG methylation levels for each sample. [Click to see an example!](./quick-example.html#cpg-methylation-matrix-methylationmat)

2. **Group information table**: ```samples_groups.tsv``` _(optional, supervised mode only)_<br> If you already have the group information and wish to compare different groups, you can provide this file to metilene3 with this [format](./quick-example.html#group-information-table-samples_groupstsv).


## Run metilene3

- [Unsupervised mode](./unsupervised.html): 
with unsupervised mode, each sample will be regarded as one group.

```yaml
python /path_to_metilene3/metilene3.py -i methylation.tsv -o /output_dir
```

Or, 

- [Supervised mode](./supervised.html):
with supervised mode, each sample should be assigned to a group, which should be recorded in the **```samples_groups.tsv```**.

```yaml
python /path_to_metilene3/metilene3.py -i methylation.tsv -g samples_groups.tsv -o /output_dir
```

More parameters could be added. Please check [unsupervised mode](./unsupervised/) and [supervised mode](./supervised/) for details.


## Output files

1. A HTML report summerizing DMRs and other results: ```/output_dir/report.html```.

2. A tab-separated table containing all DMRs found by metilene3: ```/output_dir/DMRs.tsv``` <br>_(and ```/output_dir/DMRs-unsupervised.tsv``` for DMRs found with unsupervised mode)_. <br>[Click here to understand it!](./quick-example.html#dmr-table-output_dirdmrstsv)


3. A tab-separated table containing name and order (ID) for each group: ```/output_dir/group-ID.tsv```. <br>

3. A tab-separated table containing cluster ID for each sample: ```/output_dir/clusters.tsv```. <br>_(unsupervised mode only)_

4. Figures under the folder ```/output_dir/```: <br>(_only with unsupervised mode and the parameter visualization ```-plot``` is set to True_)
	1. DMR tree: ```DMTree.[jpg, pdf]```, showing the hierarchical structure based on the sum of DMR weights (branch lengths) between two branches. You can also find the DMTree in Newick tree format: ```DMTree.nwk```.
	2. PCA 2D-visualization and clustering heatmap based on sample-level DMR methylation ratios: <br>```[PCA, heatmap].[jpg, pdf]```.

5. GSEA results: ```/output_dir/GSEA/``` _(and ```/output_dir/GSEA-unsupervised/``` for unsupervised DMRs_). <br>_(only if the parameter annotation ```-anno``` and the parameter GSEA ```-gsea``` are set.)_ 










