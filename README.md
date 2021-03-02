## Baxter Dataset

This repository holds the Baxter dataset used in the [minimalR](http://www.riffomonas.org/minimalR/) tutorials.

### `baxter.subsample.shared`

```bash
mothur "#sub.sample(shared=baxter.subsample.shared)"
mv baxter.subsample.0.03.subsample.shared baxter.subsample.shared
```

### `baxter.braycurtis.dist`

```bash
mothur "#dist.shared(shared=baxter.shared, calc=braycurtis)"
mv baxter.braycurtis.0.03.lt.dist baxter.braycurtis.dist
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
