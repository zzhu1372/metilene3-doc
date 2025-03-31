---
layout: home
---

# Data format

## Input:

### CpG methylation matrix: ```methylation.mat```
The first column should be the chromosome ID and the second column should be the position of the CpG. The following columns should be samples. Format: **tab-separated**, value range: **0-1**, missing values representated by **.** (Please do NOT use **.** to represent zero!), and genomic position **sorted**. <br> If you have ```BED``` files and don't know how to generate this matrix, click [Example](./example).

| chr | pos | sample_1 | sample_2 | sample_3 | ... |
|:-----|:-----|:-----|:-----|:-----|:-----|
| chr1 | 100 | 0.1 | 0.2 | . | ... |
| chr1 | 200 | 0.1 | 0.5 | 0.3 | ... |
| chr2 | 100 | 1 | . | 0 | ... |
| ... | ... | ... | ... | ... | ... |


### Group information table: ```samples_groups.tsv```
This table should have two columns: **ID** and **Group**. The sample IDs in this table should be exactly matched to the sample IDs in ```methylation.mat```. Format: **tab-separated**.

| ID | Group | 
|:-----|:-----|
| sample_1 | Group_A | 
| sample_2 | Group_B1 | 
| sample_3 | Group_B2 | 
| ... | ... | 


## Output:

### DMR table: ```/output_dir/DMRs.tsv```
This table contains all DMRs found by metilene3. Format: **tab-separated**, working with **iso-8859-1**.

| Column name | Description | 
|:-----|:-----|
| chr | chromosome ID. | 
| start | start position of the DMR. | 
| stop | stop position of the DMR. | 
| q | Bonferroni adjusted p-values based on MWU-test p-values. | 
| meandiff | _(for developers)_ mean difference between the methylated group and the unmethylated group. | 
| length | number of CpGs in the DMR. | 
| mwu | MWU-test p-value. | 
| p | 2D KS-test p-value. | 
| mean | mean values for each sample/group - the order (ID) of groups can be found in ```/output_dir/groupID.tsv```. | 
| sig.comparison | _(for developers)_ status of samples/groups: 1 for unmethylated, 2 for intermediate and 3 for methylated - the order (ID) of groups can be found in ```/output_dir/groupID.tsv```. | 
| meandiffabs | absolute mean difference between the methylated group and the unmethylated group. | 
| #Hypo/Int/Hyper | number of hypomethylated/intermediate/hypermethylated (Hypo/Int/Hyper)  samples/groups. | 
| meanHypo/Int/Hyper | mean of hypomethylated/intermediate/hypermethylated (Hypo/Int/Hyper) samples/groups. | 
| Hypo/Int/Hyper-samples/groups | the samples (unsupervised DMRs) or groups (supervised DMRs) that are classified as hypomethylated/intermediate/hypermethylated (Hypo/Int/Hyper). | 
| distanceToTSS | distance to the transcription start site annotated by ChIPSeeker. <br>_(optional, only if the parameter annotation ```-anno``` is set.)_ | 
| ENSEMBL | ENSEMBL ID annotated by ChIPSeeker. <br>_(optional, only if the parameter annotation ```-anno``` is set.)_ | 
| SYMBOL | gene symbol annotated by ChIPSeeker. <br>_(optional, only if the parameter annotation ```-anno``` is set.)_ | 
| anno | genomic annotation by ChIPSeeker. <br>_(optional, only if the parameter annotation ```-anno``` is set.)_ | 
| DMTree | _(for developers)_ DMRs that are associated with DMTree splits. | 















