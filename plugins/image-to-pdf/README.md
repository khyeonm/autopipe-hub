# image-to-pdf

Convert PNG or JPG image files to PDF format.

## Description

A lightweight plugin for converting image files (PNG, JPG, JPEG) to PDF. Supports both single file and batch directory conversion. Handles RGBA/transparent images by converting to RGB before export.

## Input

- PNG, JPG, or JPEG image files
- Can accept a single file path or a directory containing images

## Output

- PDF file(s) corresponding to each input image

## Usage

**Single file:**
```bash
python image_to_pdf.py /input/plot.png -o /output/plot.pdf
```

**Batch (all images in directory):**
```bash
python image_to_pdf.py /input/ -o /output/
```

## Configuration

- `input_dir`: Directory containing input images (default: `/input`)
- `output_dir`: Directory for output PDFs (default: `/output`)