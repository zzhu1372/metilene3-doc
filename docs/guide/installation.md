---
layout: home
title: "Installation"
parent: User Guide
nav_order: 1
---


# Installation
{: .no_toc }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---


## Prerequisite

- You can run metilene3 on Linux and macOS. If you are using Windows 10/11, WSL will be recommended.
<br><br>
- **If you ONLY need to call DMRs and cluster samples, you ONLY need to install:**
0. [GNU Make](https://www.gnu.org/software/make/) (usually your OS has it)
1. [Python](https://www.python.org/)
2. Python packages: [pandas](https://pandas.pydata.org/)
<br><br>
- If you wish to use **ALL functions** (e.g., annotation, visualization and GSEA), additional softwares and packages are needed:
0. [GNU Make](https://www.gnu.org/software/make/) (usually your OS has it)
1. [R](https://www.r-project.org/) and [Python](https://www.python.org/)
2. R packages: [ChIPseeker](https://bioconductor.org/packages/release/bioc/html/ChIPseeker.html) and annotation package for TxDb object (e.g., [hg19](https://www.bioconductor.org/packages/release/data/annotation/html/TxDb.Hsapiens.UCSC.hg19.knownGene.html), [hg38](https://www.bioconductor.org/packages/release/data/annotation/html/TxDb.Hsapiens.UCSC.hg38.knownGene.html), or [mm10](https://bioconductor.org/packages/release/data/annotation/html/TxDb.Mmusculus.UCSC.mm10.knownGene.html))
3. Python packages: [pandas](https://pandas.pydata.org/), [numpy](https://numpy.org/), [scikit-learn](https://scikit-learn.org/), [matplotlib](https://matplotlib.org/), [seaborn](https://seaborn.pydata.org/), [biopython](https://biopython.org/wiki/Download), [gseapy](https://github.com/zqfang/GSEApy/tree/master)


## Download and compile metilene3

- You can install metilene3 from GitHub:

```yaml
git clone https://github.com/zzhu1372/metilene3.git
cd ./metilene3
make
```
- Alternatively, you can also download it from [Download](../download.html). Extract the files and compile metilene3 under the uncompressed folder:

```yaml
cd /path_to_the_downloaded_file
tar -xvzf metilene3 x.tar.gz
cd ./metilene3
make
```