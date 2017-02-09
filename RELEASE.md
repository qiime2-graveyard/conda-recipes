# Release Notes

## Bootstrapping the Docker environment

```bash
$ docker pull condaforge/linux-anvil
$ docker run -i -t -v /path/to/conda-recipes:/src condaforge/linux-anvil:latest
# Now you should be in the linux-anvil environment
$ sed -i '/conda-forge/d' ~/.condarc
$ mkdir -p ~/.config/matplotlib
$ echo "backend: agg" > ~/.config/matplotlib/matplotlibrc
```

## Bootstrapping the 2017.2 environment for export

```bash
conda create -n qiime2-2017.2 python=3.5
source activate qiime2-2017.2

conda install -c qiime2 qiime2=2017.2.*
conda install -c qiime2 q2templates=2017.2.*
conda install -c qiime2 q2-types=2017.2.*
conda install -c qiime2 q2-feature-table=2017.2.*
conda install -c qiime2 q2-composition=2017.2.*
conda install -c qiime2 q2-diversity=2017.2.*
conda install -c qiime2 q2cli=2017.2.*
conda install -c qiime2 q2-taxa=2017.2.*
conda install -c qiime2 -c biocore q2-phylogeny=2017.2.*
conda install -c qiime2 q2-feature-classifier=2017.2.*
conda install -c qiime2 -c conda-forge q2-emperor=2017.2.*
conda install -c qiime2 q2-demux=2017.2.*
conda install -c qiime2 -c r q2-dada2=2017.2.*
conda install -c qiime2 -c bioconda q2-alignment=2017.2.*

CDPATH= R -e 'source("https://bioconductor.org/biocLite.R"); biocLite("dada2")'

# This worked with conda 4.3.9
conda list --canonical --no-pip --export --explicit > qiime2-2017.2-conda-osx-64.txt
```
