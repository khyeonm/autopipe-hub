FROM condaforge/mambaforge:latest

RUN mamba install -y -c conda-forge -c bioconda \
    pillow \
    snakemake-minimal=7.32.4 \
    python=3.11 \
    && mamba clean -afy

WORKDIR /plugin
COPY image_to_pdf.py .

WORKDIR /pipeline
COPY Snakefile .
COPY config.yaml .

CMD ["snakemake", "--cores", "1", "-p"]