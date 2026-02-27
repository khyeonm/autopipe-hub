FROM condaforge/mambaforge:latest

# Install bioinformatics tools via Bioconda
RUN mamba install -y -c bioconda -c conda-forge \
    snakemake-minimal=8.20.6 \
    gatk4=4.6.1.0 \
    samtools=1.21 \
    && mamba clean -afy

# Setup pipeline
WORKDIR /pipeline
COPY Snakefile .
COPY config.yaml .

CMD ["snakemake", "--help"]