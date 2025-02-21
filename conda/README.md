# TOGA Conda envirorment set up

## Create Conda env

```
conda env create -f toga.yml
conda activate toga
```

## Checkout TOGA Git repository

https://github.com/sanger-tol/TOGA  
which is forked and modified from:  
https://github.com/hillerlab/TOGA

The modifications are mainly:
* Skip some sanity check in the main script
* Skip git version checking
* Update config file locations
* Add nextflow lsf config template files

The checkout location on farm is:
`/software/treeoflife/bin/TOGA/`

## Config and test TOGA

```
cd TOGA
./configure.sh
./run_test.sh micro
```

## Add TOGA installation directory to the conda env path

```
cp conda/activate.d/toga_installation_activate.sh {CONDA_ENV_DIR}/etc/activate.d
cp conda/deactivate.d/toga_installation_deactivate.sh {CONDA_ENV_DIR}/etc/deactivate.d
```

## Run toga.py with your own data

```
toga.py {YOUR_DATA_PATH}/test_input/hg38.mm10.chr11.chain {YOUR_DATA_PATH}/test_input/hg38.genCode27.chr11.bed {YOUR_DATA_PATH}/test_input/hg38.2bit {YOUR_DATA_PATH}/test_input/mm10.2bit --kt --pn test -i {YOUR_DATA_PATH}/supply/hg38.wgEncodeGencodeCompV34.isoforms.txt --nc {YOUR_DATA_PATH}/nextflow_config_files --cb 3,5 --cjn 500 --u12 {YOUR_DATA_PATH}/supply/hg38.U12sites.tsv --ms --kt --nfnd
```
