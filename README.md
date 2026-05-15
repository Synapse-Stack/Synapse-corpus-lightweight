# synapse-corpus-core

Curated lightweight and medium-sized PDF stress-testing corpora extracted, normalized, and repackaged from the PDF Association SafeDocs Stressful PDF Corpus.

Designed for:

* fast CI execution
* parser regression testing
* renderer validation
* malformed PDF edge-case testing
* fuzzing pipelines
* pull request verification
* differential parser analysis

---

# Overview

This repository contains lightweight corpora intended for high-frequency automated testing workflows.

Unlike heavyweight infrastructure-scale datasets, the corpora included here are optimized for:

* GitHub Actions matrix execution
* rapid parallel testing
* minimal runner storage usage
* quick decompression
* low-cost CI pipelines

Each corpus is packaged independently as a clean `.zip` archive, allowing workflows to download only the datasets they require.

---

# Included Corpora

Current datasets include:

* androidpdfviewer
* cairo
* dejavu
* parsr
* pdfkit
* prawn
* qpdf
* react-pdf

Additional lightweight corpora may be added over time.

---

# Repository Structure

```txt id="kdr63u"
synapse-corpus-core/
├── README.md
├── LICENSE
├── .gitignore
├── manifest.json
├── SHA256SUMS
├── androidpdfviewer.zip
├── cairo.zip
├── dejavu.zip
├── parsr.zip
├── pdfkit.zip
├── prawn.zip
├── qpdf.zip
└── react-pdf.zip
```

---

# Why This Repository Exists

The original SafeDocs corpus distributions are large, monolithic, and inefficient for modern CI systems.

This repository exists to:

* avoid multi-gigabyte downloads during CI execution
* reduce GitHub Actions disk usage
* improve workflow startup speed
* enable matrix-based test execution
* isolate reusable corpora for multiple private repositories
* simplify reproducible parser testing

---

# Usage Example

Download only the required corpus during CI execution:

```bash id="jlczdb"
mkdir -p tests/assets/corpus/cairo

curl -L \
  https://media.githubusercontent.com/media/YOURORG/synapse-corpus-core/main/cairo.zip \
  -o cairo.zip

unzip -q cairo.zip -d tests/assets/corpus/cairo/

rm cairo.zip
```

---

# GitHub Actions Example

```yaml id="ohg71d"
strategy:
  matrix:
    corpus:
      - cairo
      - dejavu
      - pdfkit
      - qpdf

steps:
  - name: Fetch Corpus
    run: |
      mkdir -p tests/assets/corpus/${{ matrix.corpus }}

      curl -L \
        https://media.githubusercontent.com/media/YOURORG/synapse-corpus-core/main/${{ matrix.corpus }}.zip \
        -o corpus.zip

      unzip -q corpus.zip \
        -d tests/assets/corpus/${{ matrix.corpus }}/

      rm corpus.zip
```

---

# Recommended CI Usage

These corpora are intended for:

* pull request validation
* push-triggered workflows
* continuous fuzzing
* parser regression suites
* lightweight renderer verification

Recommended triggers:

```yaml id="dljp0g"
on:
  pull_request:

  push:
```

---

# Optimization Notes

Each archive was normalized to:

* remove unnecessary metadata
* eliminate nested archive duplication
* reduce decompression overhead
* improve extraction speed
* minimize temporary runner storage usage

Only normalized archives are stored.

Raw upstream distributions and temporary extraction artifacts are intentionally excluded.

---

# Provenance

The original datasets originate from:

* PDF Association SafeDocs Stressful Corpus
* https://labs.pdfa.org/stressful-corpus/

This repository redistributes normalized subsets strictly for testing, interoperability research, parser validation, fuzzing, and CI reproducibility purposes.

All rights remain with their respective upstream authors and projects.

---

# Integrity Verification

SHA256 hashes are provided inside:

```txt id="7ivv0l"
SHA256SUMS
```

Verification example:

```bash id="4tm7n8"
sha256sum -c SHA256SUMS
```

---

# Intended Usage

Recommended use cases include:

* PDF parser development
* malformed PDF testing
* renderer compatibility analysis
* regression validation
* fuzzing infrastructure
* differential parser testing
* automated CI pipelines
* security research

---

# License

Repository tooling, manifests, and packaging:
MIT

Corpus contents:
Owned by their respective upstream projects and contributors.

```
```
