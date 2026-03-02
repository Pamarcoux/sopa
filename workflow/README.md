# Snakemake pipeline

This directory contains the `Snakefile` that is used to run Snakemake.

use : 

for f in data/*.tif; do
  [ -f "$f" ] || continue
  sample=$(basename "$f" | cut -d. -f1)
  snakemake \
    --config data_path="$f" \
    --configfile config/phenocycler/base_20X.yaml \
    --workflow-profile profile/local \
    --cores 64 \
    --rerun-incomplete \
    all \
    2>&1 | tee "logs/${sample}.log"
done


Refer to our [getting started](https://gustaveroussy.github.io/sopa/getting_started/) to use it, or look at our [available config files](https://github.com/gustaveroussy/sopa/tree/main/workflow/config).
