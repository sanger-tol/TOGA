Combine both TOGA slum config files and Sanger nextflow profile to create the lsf templates here  
https://raw.githubusercontent.com/nf-core/configs/refs/heads/master/conf/sanger.config


Nextflow config directory must contain the following files:
1) extract_chain_features_config.nf
```
Parametes for extracting chain features.
Quite fast jobs requiring minimal memory.
One hour should be enough.
```
2) call_cesar_config_template.nf
```
Longer jobs (for example 24h)
Make sure you have the following line in this file:
process.memory = ${_MEMORY_}
Since CESAR part might split to different joblist depending on the memory requirements.
If you still like to assign a constant value here, like this:
process.memory = '50G'
then do not use --cesar_buckets parameter.
```

### Example command
```
toga.py {YOUR_DATA_PATH}/test_input/hg38.mm10.chr11.chain {YOUR_DATA_PATH}/test_input/hg38.genCode27.chr11.bed {YOUR_DATA_PATH}/test_input/hg38.2bit {YOUR_DATA_PATH}/test_input/mm10.2bit --kt --pn test -i {YOUR_DATA_PATH}/supply/hg38.wgEncodeGencodeCompV34.isoforms.txt --nc /software/treeoflife/bin/TOGA/nextflow_config_files_lsf --cb 3,5 --cjn 500 --u12 {YOUR_DATA_PATH}/supply/hg38.U12sites.tsv --ms --kt --nfnd
```