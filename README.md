# synapse-corpus-core

The PDF corpora contained in this repository originate from upstream
projects and collections referenced by the PDF Association SafeDocs
Stressful PDF Corpus project.

This repository does not claim ownership of the corpus files themselves.
All rights remain with their respective original authors and projects.


Curated lightweight PDF stress-testing corpora extracted and normalized from the PDF Association SafeDocs Stressful PDF Corpus.

Designed for:

* parser validation
* rendering regression testing
* fuzzing pipelines
* CI stress workflows
* malformed PDF edge-case testing

## Contents

This repository contains smaller and medium-sized corpora intended for high-frequency CI execution.

Current datasets include:

* androidpdfviewer
* cairo
* dejavu
* parsr
* pdfkit
* prawn
* qpdf
* react-pdf

Each corpus is packaged independently as a clean `.zip` archive to allow selective downloads during GitHub Actions workflows.

## Purpose

The goal of this repository is to:

* avoid downloading multi-gigabyte monolithic archives
* reduce GitHub Actions storage pressure
* enable matrix-based CI execution
* improve reproducibility for parser and renderer testing

## Upstream Source

The original datasets originate from:

* PDF Association SafeDocs Stressful Corpus
* https://labs.pdfa.org/stressful-corpus/

This repository only redistributes normalized subsets for CI and testing convenience.

All rights remain with their respective upstream authors and projects.

## Usage Example

```bash
curl -L \
  https://media.githubusercontent.com/media/YOURORG/synapse-corpus-core/main/cairo.zip \
  -o cairo.zip

unzip cairo.zip
```

## Recommended Usage

This repository is intended for:

* pull request validation
* lightweight regression testing
* parser differential analysis
* continuous fuzzing workflows

## License

Repository tooling and packaging:
MIT

Corpus content:
Owned by respective upstream projects and contributors.

```
```
