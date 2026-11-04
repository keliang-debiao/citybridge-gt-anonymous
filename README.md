CityBridge-GT

This repository contains the anonymous PyTorch code package for CityBridge-GT: A Leakage-Controlled Dual-Space Graph Transformer for Cross-City Next-POI Prediction in Smart Tourism.

The package provides the model implementation, data-processing pipeline, experiment configuration files, command-line interfaces, evaluation utilities, statistical analysis tools, documentation, tests, and example artifacts required to inspect and run the code.

Repository Structure

citybridge_gt/
├── .github/workflows/       # Continuous-integration configuration
├── assets/                  # Manuscript reference-table data
├── configs/                 # Model and experiment configurations
├── docs/                    # Technical and reproducibility documentation
├── evidence/                # Included example and verification artifacts
├── examples/                # Simulated log-format examples
├── scripts/                 # Experiment and repository utility scripts
├── src/citybridge/          # Main Python package
├── tests/                   # Automated tests
├── CITATION.cff             # Software citation metadata
├── Dockerfile               # Container environment definition
├── LICENSE                  # MIT license
├── pyproject.toml           # Package metadata and build configuration
├── requirements.txt         # Runtime dependencies
├── requirements-lock-cpu.txt # Locked CPU environment dependencies
├── SHA256SUMS.json          # File-integrity manifest
└── START_HERE_ZH.md         # Chinese quick-start guide

Core Python Package

The main implementation is located in src/citybridge/.

File

Included functionality

model.py

CityBridge-GT neural architecture, including POI identity embeddings, shared prototype representations, evidence-aware gating, graph attention layers, causal trajectory encoding, periodic retrieval and fusion, domain adapters, interval prediction, and candidate scoring.

data.py

Canonical event loading, validation, deduplication, session construction, causal prefix generation, temporal-fold splitting, train-only feature fitting, graph construction, split encoding, and preprocessing audits.

convert.py

Local-data converters for the supported Foursquare-style and Gowalla-CA input formats, together with taxonomy, geographic-boundary, timezone, and provenance handling.

engine.py

Source-domain training, target-city adaptation, checkpoint management, prediction, evaluation, perturbation handling, calibration, environment capture, and run metadata generation.

metrics.py

Ranking, per-event, calibration, and temperature-scaling utilities.

statistics.py

Fold/seed aggregation, paired visitor-cluster inference, subgroup comparison, bootstrap procedures, permutation procedures, and Holm correction.

baseline.py

Transparent popularity and Markov sanity baselines.

demo.py

Toy trajectory generation, reduced demonstration configuration, smoke-workflow orchestration, and simulated log generation.

cli.py

Command-line entry points for conversion, preparation, training, evaluation, calibration, aggregation, inference, baselines, toy data, ablations, and stress tests.

util.py

Configuration loading, deterministic seeding, JSON serialization, hashing, environment reporting, and manifest generation.

__main__.py

Module entry point for python -m citybridge.

__init__.py

Package version metadata.

Model Components

The implementation includes the following CityBridge-GT components:

city-specific POI identity embeddings;

a shared prototype dictionary for cross-city representation;

descriptor-based prototype assignment;

evidence-aware fusion of identity and prototype representations;

multi-relation graph encoding with spatial, transition, and semantic relations;

time, weekday, category, position, and elapsed-time encoding;

a causal trajectory Transformer;

periodic-state retrieval and gated state fusion;

domain-specific low-rank adapters;

next-POI candidate scoring with transition, category, and reachability terms;

auxiliary time-interval and category objectives;

cross-city representation alignment;

source-city training and target-city adaptation controls.

Configuration Files

The configs/ directory contains:

paper.yaml: the complete experiment configuration, including preprocessing, model, optimization, loss, calibration, and seed settings;

smoke.yaml: a reduced configuration for lightweight pipeline inspection.

Experiment Scripts

The scripts/ directory contains:

Script

Purpose

run_suite.py

Coordinates data preparation, temporal folds, source training, target-city adaptation, validation/test prediction generation, calibration, and aggregation.

validation_search.py

Performs validation-only coordinate search over selected model and preprocessing settings.

export_tables.py

Converts aggregated JSON summaries into tabular CSV files.

plot_results.py

Produces fold-level plots from repository-generated summary files.

efficiency_summary.py

Summarizes recorded training-time, memory, device, and parameter information.

anonymous_audit.py

Scans repository files for common identity, path, credential, and metadata traces.

submission_gate.py

Checks the presence and type of repository artifacts required by the submission workflow.

Documentation

The docs/ directory contains:

AI_EXPERIMENT_GUIDE_ZH.md: Chinese experiment and AI-handoff guide;

ANONYMOUS_SUBMISSION.md: anonymous repository preparation notes;

BASELINES.md: baseline integration and provenance requirements;

DATA.md: canonical data schema, source preparation, and preprocessing contracts;

IMPLEMENTATION_DECISIONS.md: implementation conventions and design choices;

LOGS.md: log locations, formats, and command records;

PAPER_CODE_MAP.md: mapping between manuscript components and source files;

REPRODUCIBILITY_STATUS.md: inventory of available and required reproducibility artifacts.

Tests

tests/test_core.py contains automated checks for core repository behavior, including data boundaries, temporal splitting, graph construction, freeze masks, model outputs, ranking metrics, calibration, deterministic execution, aggregation rules, and statistical utilities.

The .github/workflows/ci.yml file defines the repository's automated test workflow.

Included Artifacts

The package also contains:

synthetic trajectory files used by the example workflow;

prepared split and graph-asset examples;

example checkpoints, prediction files, logits, targets, calibration files, and metadata;

simulated JSONL log-format examples;

environment, integrity, determinism, test, audit, and submission-check records;

manuscript reference tables stored separately from the training and evaluation code;

a repository-wide SHA-256 file manifest.

These files are organized under evidence/, examples/, and assets/ according to their role.

Software Environment

The package is configured for Python 3.11 or 3.12 and includes pinned dependencies for:

PyTorch;

NumPy;

SciPy;

PyYAML;

Matplotlib.

pyproject.toml defines the installable citybridge-gt package and the citybridge command-line entry point. Dockerfile provides a container definition, while requirements-lock-cpu.txt records the locked CPU dependency set included with the archive.

License and Citation

The newly written source code is distributed under the MIT License. Software citation metadata is provided in CITATION.cff.
