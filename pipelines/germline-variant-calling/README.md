# Germline Variant Calling Pipeline

Germline variant calling using GATK HaplotypeCaller from aligned BAM files.

## Workflow

```
BAM → GATK CreateSequenceDictionary (if missing) → GATK HaplotypeCaller → VCF.gz
```

## Required Inputs

| File | Description |
|------|-------------|
| `*.bam` + `*.bam.bai` | Aligned BAM file with index |
| Reference `.fa` + `.fai` | Reference genome with index |

## How to Run

```bash
docker build -t germline-variant-calling pipelines/germline-variant-calling/
docker run --rm \
  -v /path/to/ref:/ref \
  -v /path/to/bams:/input:ro \
  -v /path/to/output:/output \
  germline-variant-calling \
  snakemake --cores 8 -p
```