![GitHub License](https://img.shields.io/github/license/chenyiru3/simple-pyper)
![PyPI - Version](https://img.shields.io/pypi/v/process-hdst?style=flat-square)

# HDSTDb Spatial Transcriptomics Data Preprocessing

Welcome to the Spatial Transcriptomics Data Preprocessing package for data downloaded from HDSTDb. This tool is designed to facilitate the processing of spatial transcriptomics data using anndata objects, especially anndata from our database, HDSTDb. It offers a comprehensive pipeline for quality control, clustering, and analysis of highly variable genes, co-occurrence, and neighborhood enrichment.

As we point out in the database website, the anndatas all clustered multiple leiden resolutions processing, but the website only contains analysis results with one specific resolution of each sample. User can download annadata and choose interested resolution to run a result report.

## Features

- **Load and preprocess spatial transcriptomics data**: Efficiently manage and manipulate data stored in the anndata format.
- **Perform quality control**: Identify and filter out low-quality data.
- **Execute Leiden clustering**: Cluster data using the Leiden algorithm with customizable resolution.
- **Identify highly variable genes**: Discover genes that show significant expression variability.
- **Analyze co-occurrence patterns**: Examine the spatial co-occurrence of gene expression.
- **Conduct neighborhood enrichment analysis**: Investigate spatial relationships and enrichment in data.
- **Save processed metadata**: Store and manage metadata for further analysis.

## Installation

To install this package, make sure you have Python installed (preferably Python 3.7 or later). You can install the package via pip:

```bash
pip install your-package-name
```

Replace `your-package-name` with the actual name of your package on PyPI.

## Usage

This package provides a command line interface (CLI) for easy execution of preprocessing tasks. Below are detailed instructions on how to use the CLI.

### Command Line Interface

To run the preprocessing, use the following command structure:

```bash
python -m your_package.cli <adata_path> <work_path> [options]
```

- **`adata_path`**: The file path to your anndata object (e.g., `data/adata.h5ad`).
- **`work_path`**: The directory path where you want the results to be saved (e.g., `output`).

### Available Options

- **`--version`**: Display the version number of the package and exit.
  
- **`--leiden_key`**: Specify a key for Leiden clustering. This key is used to refer to the clustering results within the anndata object.

- **`--after_leiden`**: Perform additional processing steps after Leiden clustering has been executed.

- **`--leiden_resolution`**: Set the resolution parameter for the Leiden clustering algorithm. The default is 1.0, but you can adjust this to alter the granularity of the clusters.

- **`--all`**: Execute all available processing steps, including quality control, clustering, and all analysis steps.

- **`--qc`**: Perform quality control to filter and clean the data.

- **`--leiden`**: Execute Leiden clustering on the data.

- **`--hvg`**: Identify highly variable genes within the dataset.

- **`--co_occurrence`**: Analyze the co-occurrence of gene expressions spatially.

- **`--nhood_enrichment`**: Perform neighborhood enrichment analysis to identify spatial patterns and relationships.

- **`--save_metadata`**: Save the metadata from the preprocessing steps to the specified output directory.

### Example Usages

#### Running All Steps

If you want to perform all available preprocessing steps on an anndata object located at `data/adata.h5ad` and save the results to a directory named `results` inside `output`, use the following command:

```bash
python -m your_package.cli data/adata.h5ad output --all
```

This will sequentially perform quality control, Leiden clustering, and all analysis steps, saving the results in `output/results`.

#### Running Specific Steps

If you're interested in performing only specific steps, such as quality control and Leiden clustering with a specific resolution, you can specify these options separately:

```bash
python -m your_package.cli data/adata.h5ad output --qc --leiden --leiden_resolution 0.5
```

This command will conduct quality control and then apply Leiden clustering with a resolution of 0.5, saving the intermediate and final results in the specified output directory.

#### Post-Leiden Processing

To perform further analysis after Leiden clustering, ensure you specify the Leiden key:

```bash
python -m your_package.cli data/adata.h5ad output --after_leiden --leiden_key my_leiden_key
```

Here, replace `my_leiden_key` with the actual key used for Leiden clustering in your dataset.

### Error Handling

If an error occurs during the Leiden clustering process, the script will default to using standard parameters: a Leiden key of `leiden` and a resolution of 1.0. This ensures that the process can continue with default settings if custom parameters cause issues.

## Contributing

We welcome contributions to enhance the functionality of this package. If you wish to contribute, please follow these steps:

1. **Fork the repository** on GitHub.
2. **Create a new branch** for your feature or bug fix.
3. **Make your changes**, ensuring you include tests for any new features.
4. **Submit a pull request** with a clear description of your changes and the problem they solve.

## License

This project is licensed under the MIT License, allowing for flexible use and modification.

## Contact

For questions, comments, or suggestions, please open an issue on GitHub or contact the maintainer directly. We'd love to hear your feedback and are here to help with any problems you encounter.

