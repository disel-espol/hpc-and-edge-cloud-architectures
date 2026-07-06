# How Are HPC, Edge, and Serverless Architectures Built in the Cloud Continuum?

## An Analysis of Real Cloud Architectures in AWS

Reproducibility package for the journal paper *“How Are HPC, Edge, and Serverless Architectures Built in the Cloud Continuum? An Analysis of Real Cloud Architectures in AWS”* by Steven Santillán and [Cristina L. Abad](https://sites.google.com/fiec.espol.edu.ec/cv-cabad/english) from [ESPOL University](https://www.espol.edu.ec/en).

This package contains the processed datasets and Jupyter notebooks required to reproduce the analyses reported in the paper. The study investigates how real-world AWS cloud architectures are built across the cloud continuum, with particular focus on High-Performance Computing (HPC), Edge, Serverless, Function-as-a-Service (FaaS), Serverless Compute, and Event-Driven architectures.

The workflow is organized into independent notebooks. Each notebook reproduces a specific analytical component using the processed datasets included in this directory and, when required, the public Cloudscape GraphML repository.

## Package Structure

```text
Journal_paper/
├── architectures_with_services.pkl
├── classified_architectures_with_metadata.csv
│
├── 01_analyze_architecture_characteristics.ipynb
├── 02_analyze_graph_metrics.ipynb
├── 03_mine_frequent_graph_patterns.ipynb
├── 04_analyze_temporal_trends.ipynb
└── README.md
```

## Datasets

### `architectures_with_services.pkl`

Intermediate dataset containing the identifier of each Cloudscape architecture and the AWS services extracted from its GraphML representation.

This file preserves the service lists in Python format and supports analyses that require direct processing of the services associated with each architecture.

### `classified_architectures_with_metadata.csv`

Processed dataset used throughout this reproducibility package. It includes:

- Architecture identifiers and metadata.
- Architecture names, descriptions, categories, and source links.
- Extracted AWS services.
- Internal architecture labels.
- Analytical membership flags for HPC, Edge, Serverless, None, Strictly Edge, FaaS, Serverless Compute, and Event-Driven categories.
- Detected Serverless services and their corresponding subcategories.

## Reproducibility Notebooks

### 1. [Analyze Architecture Characteristics](./01_analyze_architecture_characteristics.ipynb)

This is the main descriptive-analysis notebook. It uses the processed architecture datasets to reproduce analyses of:

- The distribution of architectures across HPC, Edge, Serverless, None, Strictly Edge, and FaaS categories.
- AWS service usage by analytical category.
- Discriminating services for HPC, Edge, Serverless, Strictly Edge, and FaaS architectures.
- Storage-service and machine-learning-service usage.
- Service co-occurrences and intersections between architectural categories.
- Industry and workflow characteristics.
- Figures, tables, and supporting CSV files used in the paper.

### 2. [Analyze Graph Metrics](./02_analyze_graph_metrics.ipynb)

This notebook computes graph-based metrics for the Cloudscape architecture graphs, including:

- Number of nodes.
- Number of edges.
- Graph density.
- Average degree.
- Maximum path length.
- Additional structural graph characteristics by analytical category.

### 3. [Mine Frequent Graph Patterns](./03_mine_frequent_graph_patterns.ipynb)

This notebook applies gSpan-based frequent subgraph mining to the Cloudscape architecture graphs. It includes:

- Global frequent-pattern mining.
- Category-specific frequent-pattern mining.
- Normalized support computation by category.
- Comparison of patterns across HPC, Edge, Serverless, FaaS, and related analytical categories.
- Bootstrap-based validation of frequent patterns and their stability.

### 4. [Analyze Temporal Trends](./04_analyze_temporal_trends.ipynb)

This notebook analyzes the temporal evolution of the studied cloud architectures. It includes:

- Retrieval of YouTube video publication years associated with Cloudscape architectures.
- Annual counts of architectures by analytical category.
- Absolute and percentage-based temporal trends.
- Export of temporal-trend figures and supporting CSV files.

To reproduce the video-year retrieval step in Google Colab, a YouTube Data API v3 key must be stored as a Colab Secret named:

```text
Api-YT
```

## Recommended Execution Order

The notebooks are independent reproducibility components rather than a single monolithic workflow. A recommended execution order is:

1. Run `01_analyze_architecture_characteristics.ipynb` to reproduce descriptive analyses and category-based results.
2. Run `02_analyze_graph_metrics.ipynb` to reproduce graph structural metrics.
3. Run `03_mine_frequent_graph_patterns.ipynb` to reproduce gSpan pattern mining and bootstrap validation.
4. Run `04_analyze_temporal_trends.ipynb` to reproduce the temporal analysis.

The graph-metrics and gSpan notebooks independently clone Cloudscape to obtain the original GraphML files. They do not require the main-analysis notebook to be executed beforehand.

## Requirements

The notebooks use Python and rely primarily on the following packages:

```text
pandas
numpy
networkx
lxml
matplotlib
gspan-mining
requests
tqdm
```

Google Colab is recommended because the notebooks were developed and executed in that environment.

## How to Cite

Citation details will be added after the journal paper is accepted or published.

## Related Reproducibility Package

For the previous workshop study, see the [reproducibility package for *“An Analysis of HPC and Edge Architectures in the Cloud”*](../Workshop_paper/README.md).

## External Data Source

The original cloud architecture graphs are obtained from the public [Cloudscape repository](https://github.com/WiscADSL/Cloudscape).

