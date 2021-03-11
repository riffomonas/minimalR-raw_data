## Baxter Dataset

This repository holds the Baxter dataset used in the [minimalR](http://www.riffomonas.org/minimalR/) tutorials.

### `baxter.subsample.shared`

```bash
mothur "#sub.sample(shared=baxter.shared)"
mv baxter.0.03.subsample.shared baxter.subsample.shared
```

### `baxter.braycurtis.dist`

```bash
mothur "#dist.shared(shared=baxter.shared, calc=braycurtis, output=square)"
mv baxter.braycurtis.0.03.square.dist baxter.braycurtis.dist
```

### `baxter.groups.ave-std.summary`

```bash
mothur "#summary.single(shared=baxter.shared, calc=nseqs-sobs-shannon-invsimpson-coverage, subsample=TRUE)"
```


### `baxter.braycurtis.pcoa.axes` / `baxter.braycurtis.pcoa.loadings`

```bash
mothur "#pcoa(phylip=baxter.braycurtis.dist)"
```


### `baxter.braycurtis.nmds_2d.axes` / `baxter.braycurtis.nmds_2d.stress`

```bash
mothur "#nmds(phylip=baxter.braycurtis.dist, maxdim=2)"
rm baxter.braycurtis.nmds.iters
mv baxter.braycurtis.nmds.axes baxter.braycurtis.nmds_2d.axes
mv baxter.braycurtis.nmds.stress baxter.braycurtis.nmds_2d.stress
```


### `baxter.braycurtis.nmds_3d.axes` / `baxter.braycurtis.nmds_3d.stress`

```bash
mothur "#nmds(phylip=baxter.braycurtis.dist, mindim=3)"
rm baxter.braycurtis.nmds.iters
mv baxter.braycurtis.nmds.axes baxter.braycurtis.nmds_3d.axes
mv baxter.braycurtis.nmds.stress baxter.braycurtis.nmds_3d.stress
```


### `baxter.rarefaction`

```bash
mothur "#rarefaction.single(shared=baxter.shared)"
mv baxter.groups.rarefaction baxter.rarefaction
```


## Schubert Dataset

### Get raw data files

```bash
wget -N https://github.com/SchlossLab/Schubert_clinical_mBio_2014/raw/master/data/process/schubert.metadata.xlsx
wget -N https://github.com/SchlossLab/Schubert_clinical_mBio_2014/raw/master/data/process/schubert.shared.gz
wget -N https://github.com/SchlossLab/Schubert_clinical_mBio_2014/raw/master/data/process/schubert.cons.taxonomy.gz

gunzip schubert.shared.gz schubert.cons.taxonomy.gz
```

Not everything in the metadata is in the shared file. Need to join on the dataframes

```R
library(tidyverse)
library(readxl)

md <- read_xlsx("schubert.metadata.xlsx") %>% select(sample_id)

read_tsv("schubert.shared") %>%
  inner_join(., md, by=c("Group" = "sample_id")) %>%
  write_tsv("schubert.shared")
```


### `schubert.subsample.shared`

```bash
mothur "#sub.sample(shared=schubert.shared)"
mv schubert.0.03.subsample.shared schubert.subsample.shared
```

### `schubert.braycurtis.dist`

```bash
mothur "#dist.shared(shared=schubert.shared, calc=braycurtis, output=square)"
mv schubert.braycurtis.0.03.square.dist schubert.braycurtis.dist
```

### `schubert.groups.ave-std.summary`

```bash
mothur "#summary.single(shared=schubert.shared, calc=nseqs-sobs-shannon-invsimpson-coverage, subsample=TRUE)"
```


### `schubert.braycurtis.pcoa.axes` / `schubert.braycurtis.pcoa.loadings`

```bash
mothur "#pcoa(phylip=schubert.braycurtis.dist)"
```


### `schubert.braycurtis.nmds_2d.axes` / `schubert.braycurtis.nmds_2d.stress`

```bash
mothur "#nmds(phylip=schubert.braycurtis.dist, maxdim=2)"
rm schubert.braycurtis.nmds.iters
mv schubert.braycurtis.nmds.axes schubert.braycurtis.nmds_2d.axes
mv schubert.braycurtis.nmds.stress schubert.braycurtis.nmds_2d.stress
```


### `schubert.braycurtis.nmds_3d.axes` / `schubert.braycurtis.nmds_3d.stress`

```bash
mothur "#nmds(phylip=schubert.braycurtis.dist, mindim=3)"
rm schubert.braycurtis.nmds.iters
mv schubert.braycurtis.nmds.axes schubert.braycurtis.nmds_3d.axes
mv schubert.braycurtis.nmds.stress schubert.braycurtis.nmds_3d.stress
```


### `schubert.rarefaction`

```bash
mothur "#rarefaction.single(shared=schubert.shared)"
mv schubert.groups.rarefaction schubert.rarefaction
```
