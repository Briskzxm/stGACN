# stGACN

`stGACN` is a Python package for quantitative characterization and interpretation of rare spatial heterogeneity from spatial transcriptomics data. 

![View the PDF](./Framework.jpg)

### Installation
Users need to create an environment and install stGACN by following procedures:
```
conda create -n stGACN_env python=3.8
conda activate stGACN_env
pip install -r requirements.txt
pip install stGACN
```
### Usage
Input data of stGACN :
- The input files include various data formats, with `h5ad` being a representative example containing spatial transcriptomics data with spatial coordinates stored in `.obsm[‘spatial’]`.

```
import scanpy as sc
file_path = '/home/user/data/spatial_data.h5ad'
adata = sc.read(file_path)
```

The definition and training step of stGACN are carried out as follows:
```
# model definition  
model = stGACN.stGACN(adata,device=device)
# model training
adata = model.train()
```

Subsequently, clustering analysis can be performed using algorithms such as `mclust` or `leiden`.

**Note:** Before using the `mclust` algorithm, make sure to install the `mclust` package in R and configure `os.environ['R_HOME']` with the correct path.

```
# Apply clustering algorithm
from stGACN.utils import clustering
clustering(adata, n_clusters)
```

## Tutorial
Please see the Jupyter notebook in the **Tutorial** folder. It includes several tutorials, providing examples across different species, sequencing technologies, and diseases.

## License
This project is covered under the **MIT License**.

