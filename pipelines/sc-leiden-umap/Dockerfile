FROM condaforge/mambaforge:latest

# Install scanpy and dependencies for single-cell analysis
RUN mamba install -y -c conda-forge -c bioconda \
    snakemake-minimal \
    scanpy=1.10.4 \
    leidenalg=0.10.2 \
    python-igraph \
    matplotlib \
    pandas \
    numpy \
    && mamba clean -afy

# Setup pipeline
WORKDIR /pipeline
COPY Snakefile .
COPY config.yaml .
COPY scripts/ scripts/

CMD ["snakemake", "--cores", "1", "-p"]