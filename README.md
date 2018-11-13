## MitoFisher Instructions

MitoFisher is a pipeline for extracting mitochondrial or chloroplast genomes from NGS data, this can be whole genome sequencing or any other kind of sequencing where significant amounts of plastid genomes are present. For example, chloroplasts and mitochondria are often found as "bycatch" in bait-capture experiments thanks to their abundance.


## Install docker

On windows:

https://docs.docker.com/docker-for-windows/install/

On Ubuntu:

sudo apt install docker.io

On Mac:

https://docs.docker.com/docker-for-mac/install/


## Build the docker image

You may have to login first with:
```markdown
docker login
```

Then run 

```markdown
`docker build -t mito_pipeline .`
```

## Set up the Folders
```markdown
├── mito_pipeline.snakefile
├── raw
│ ├── 1_1.fq.gz
| |
│ └── 1_2.fq.gz
├── ref
| |
│ └── example.fasta
```
## Run the pipeline

# On Windows 

You may have to share a drive in docker settings (right click docker logo, click settings and then Shared Drives.)

Make sure that you've allocated as much resources as possible, right click docker logo, settings, advanced, give it one less cpu than the max and as much memory as you can spare.

Open Windows Powershell, and change to the directory set up in the previous step

Then run:
```markdown
docker run --rm -it -v ${PWD}:/work mito_pipeline snakemake --snakefile mito_pipeline.snakefile --cores 8
```
changing the number of cores to the number of cpu's set in docker settings.



