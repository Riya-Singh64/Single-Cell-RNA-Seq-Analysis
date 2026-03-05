# Single-Cell-RNA-Seq-Analysis
Single Cell RNA Sequencing Analysis Pipeline using Scanpy

# Single Cell RNA Sequencing Analysis Pipeline using Scanpy

## Introduction
Single-cell RNA sequencing (scRNA-seq) is a sequencing technique used to study gene expression at the individual cell level. Unlike bulk RNA sequencing, which measures the average expression across many cells, scRNA-seq allows researchers to identify cellular heterogeneity and discover distinct cell populations.

In this pipeline, a scRNA-seq dataset from GEO was analyzed using the Scanpy Python framework. The goal was to perform clustering of cells and identify marker genes for different cell populations.

---

## Dataset

**Dataset Source:** NCBI GEO

Datasets used:
- GSE164898
- GSE223886

**Samples used**

Healthy samples (GSE164898):
- GSM5022599
- GSM5022603

Cancer samples (GSE223886):

BRCA1:
- GSM6998341
- GSM6998343

BRCA2:
- GSM6998337
- GSM6998340

**Data format**

10x Genomics filtered_feature_bc_matrix (.h5)

---

## Tools Used

- Python
- Scanpy
- Anndata
- Pandas
- NumPy
- Matplotlib

**Main tool:** Scanpy – Python toolkit for single-cell analysis

---

## scRNA-seq Analysis Workflow

The following steps were performed in the pipeline:

1. Data Loading  
2. Quality Control  
3. Normalization  
4. Highly Variable Gene Selection  
5. Dimensionality Reduction (PCA)  
6. Graph Construction  
7. Cell Clustering using Leiden Algorithm  
8. Visualization using UMAP  
9. Differential Gene Expression  
10. Marker Gene Identification  

**Algorithm used:** Leiden Clustering Algorithm

---

## Cell Clustering using Leiden Algorithm

Cell clustering is a key step in single-cell RNA sequencing analysis. After dimensionality reduction and graph construction, clustering algorithms are used to group cells with similar gene expression profiles.

In this project, the Leiden algorithm was used to identify cell clusters. The algorithm works by optimizing modularity in a graph representation of the data and detecting communities of cells.

### Steps involved

1. Construction of a k-nearest neighbor graph  
2. Identification of communities using the Leiden algorithm  
3. Assignment of cluster labels to each cell  

### Code

```python
sc.pp.neighbors(adata)
sc.tl.leiden(adata)
```
Visualization

1. UMAP Visualization

UMAP (Uniform Manifold Approximation and Projection) was used to visualize the cell clusters in two dimensions. Each point

represents a single cell, and cells with similar gene expression profiles appear closer together in the plot.

### Code

```python
sc.tl.umap(adata)
sc.pl.umap(adata, color="leiden")
```
2. Dot Plot of Marker Genes

Dot plots were used to visualize the expression of marker genes across different clusters.

The size of the dot represents the percentage of cells expressing the gene, while the color intensity indicates the average 

expression level.

### Code

```python
sc.pl.rank_genes_groups_dotplot(adata)
```

3. Heatmap of Marker Genes

Heatmaps were used to display the expression patterns of top marker genes across different clusters. This helps identify 

genes that are highly expressed in specific cell populations.

### Code

```python
sc.pl.rank_genes_groups_heatmap(adata, n_genes=10)
```

Results

The analysis successfully identified distinct cell clusters within the dataset. Differential gene expression analysis 

revealed marker genes associated with each cluster. These marker genes help characterize specific cell populations present 

in the tumor microenvironment.

Conclusion

This project demonstrates a basic single-cell RNA sequencing analysis pipeline using Scanpy. The workflow includes quality

control, normalization, clustering, visualization, and marker gene identification. Such analyses are widely used in cancer

research to understand cellular heterogeneity and identify potential therapeutic targets.
