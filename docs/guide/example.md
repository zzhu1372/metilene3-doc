---
layout: home
title: "Example"
parent: User Guide
nav_order: 7
---

This is an example of how to prepare the input file(s) and run metilene3. You should have a table of your samples and a folder with BED files. Here, we use Python3 and bedtools.

```python
import os
import pandas as pd
```

Load the table that contains sample IDs, group information (if you want to use supervised mode) and names of BED files:

```python
df = pd.read_excel('samples.xlsx')
df[['ID','Group']].to_csv("group.tsv", sep='\t', index=False,)
df[['ID','Group','bedfile']].head(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>ID</th>
      <th>Group</th>
      <th>bedfile</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>S0</td>
      <td>Blood-T</td>
      <td>S0.bed</td>
    </tr>
    <tr>
      <th>1</th>
      <td>S100</td>
      <td>Blood-B</td>
      <td>S100.bed</td>
    </tr>
    <tr>
      <th>2</th>
      <td>S101</td>
      <td>Blood-NK</td>
      <td>S101.bed</td>
    </tr>
    <tr>
      <th>3</th>
      <td>S102</td>
      <td>Blood-T</td>
      <td>S102.bed</td>
    </tr>
    <tr>
      <th>4</th>
      <td>S103</td>
      <td>Blood-T</td>
      <td>S103.bed</td>
    </tr>
  </tbody>
</table>
</div>



Use bedtools to merge all BED files to a matrix:

```python
os.system('cd /path_to_BEDfiles/;\
bedtools unionbedg -i '+(df['bedfile']+' ').sum()+\
'-header -names '+(df['ID']+' ').sum()+\
'-filler NA > ./input.raw')
```


Load the merged matrix and convert it to the metilene3 format:

```python
met = pd.read_table('./input.raw')
met = met.drop(columns='start')
met.to_csv("./input.tsv", sep='\t', index=False, float_format='%.3f', na_rep='.')
met.head(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>chrom</th>
      <th>end</th>
      <th>S0</th>
      <th>S100</th>
      <th>S101</th>
      <th>S102</th>
      <th>S103</th>
      <th>S104</th>
      <th>S105</th>
      <th>S106</th>
      <th>...</th>
      <th>S91</th>
      <th>S92</th>
      <th>S93</th>
      <th>S94</th>
      <th>S95</th>
      <th>S96</th>
      <th>S97</th>
      <th>S98</th>
      <th>S99</th>
      <th>S9</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>chr1</td>
      <td>10470</td>
      <td>0.666667</td>
      <td>NaN</td>
      <td>0.675000</td>
      <td>0.625000</td>
      <td>0.575000</td>
      <td>0.652174</td>
      <td>0.760000</td>
      <td>0.552632</td>
      <td>...</td>
      <td>0.690476</td>
      <td>0.700000</td>
      <td>0.562500</td>
      <td>0.708333</td>
      <td>0.875000</td>
      <td>0.700000</td>
      <td>0.968750</td>
      <td>0.550000</td>
      <td>0.727273</td>
      <td>0.774194</td>
    </tr>
    <tr>
      <th>1</th>
      <td>chr1</td>
      <td>10472</td>
      <td>0.600000</td>
      <td>0.900000</td>
      <td>0.725000</td>
      <td>0.800000</td>
      <td>0.846154</td>
      <td>0.869565</td>
      <td>0.750000</td>
      <td>0.625000</td>
      <td>...</td>
      <td>0.880952</td>
      <td>0.750000</td>
      <td>0.740000</td>
      <td>0.863636</td>
      <td>0.833333</td>
      <td>0.633333</td>
      <td>0.968750</td>
      <td>0.625000</td>
      <td>0.909091</td>
      <td>0.882353</td>
    </tr>
    <tr>
      <th>2</th>
      <td>chr1</td>
      <td>10485</td>
      <td>0.875000</td>
      <td>0.909091</td>
      <td>0.682927</td>
      <td>0.904762</td>
      <td>0.790698</td>
      <td>0.846154</td>
      <td>0.814815</td>
      <td>0.727273</td>
      <td>...</td>
      <td>0.886364</td>
      <td>0.818182</td>
      <td>0.758621</td>
      <td>0.800000</td>
      <td>0.958333</td>
      <td>0.812500</td>
      <td>0.976744</td>
      <td>0.795918</td>
      <td>0.962963</td>
      <td>0.897436</td>
    </tr>
    <tr>
      <th>3</th>
      <td>chr1</td>
      <td>10490</td>
      <td>0.882353</td>
      <td>1.000000</td>
      <td>0.860465</td>
      <td>1.000000</td>
      <td>0.795455</td>
      <td>0.827586</td>
      <td>0.964286</td>
      <td>0.767442</td>
      <td>...</td>
      <td>0.866667</td>
      <td>0.878788</td>
      <td>0.896552</td>
      <td>0.920000</td>
      <td>0.875000</td>
      <td>0.787879</td>
      <td>1.000000</td>
      <td>0.843137</td>
      <td>0.896552</td>
      <td>0.925000</td>
    </tr>
    <tr>
      <th>4</th>
      <td>chr1</td>
      <td>10494</td>
      <td>0.705882</td>
      <td>0.818182</td>
      <td>0.813953</td>
      <td>1.000000</td>
      <td>0.727273</td>
      <td>0.678571</td>
      <td>0.586207</td>
      <td>0.642857</td>
      <td>...</td>
      <td>0.911111</td>
      <td>0.764706</td>
      <td>0.766667</td>
      <td>0.760000</td>
      <td>0.791667</td>
      <td>0.848485</td>
      <td>0.979167</td>
      <td>0.673077</td>
      <td>0.933333</td>
      <td>0.875000</td>
    </tr>
  </tbody>
</table>
</div>



Run metilene3 with unsupervised mode:

```python
os.system('python /path_to_metilene3/metilene3.py \
  -i ./input.tsv \
  -o ./results_unsupervised')
```

Or, run metilene3 with supervised mode:

```python
os.system('python /path_to_metilene3/metilene3.py \
  -i ./input.tsv \
  -g ./group.tsv \
  -o ./results_supervised')
```

Finally you can find the results under ```./results_unsupervised``` or ```./results_supervised```.