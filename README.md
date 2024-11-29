# stGACN

`stGACN` is a Python package for quantitative characterization and interpretation of rare spatial heterogeneity from spatial transcriptomics data. 

![View the PDF](./Framework.jpg)

### Installation
**Note:** Before using the `mclust` algorithm, ensure that the `mclust` package is installed in R and that `os.environ['R_HOME']` is configured with the correct path by following these steps:

```
conda create -n stGACN_env python=3.8
conda activate stGACN_env
conda install r-base
pip install rpy2==3.4.1
R --quiet --no-restore
install.packages('mclust')
```
Next, we will set up the environment required for stGACN：
```
pip install -r requirements.txt
pip install stGACN
```
**Note:** During the installation process, you might encounter issues with the installation of `torch_sparse`, `torch_scatter`, or `torch_geometric`. If this happens, you will need to manually download the `.whl` files from [PyTorch Geometric WHL](https://pytorch-geometric.com/whl/). 

Once downloaded, install the files using the following command (replace `<file_name>.whl` with the actual filename of the `.whl` file):
```
pip install <file_name>.whl
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

```
# Apply clustering algorithm
from stGACN.utils import clustering
clustering(adata, n_clusters)
```

## Tutorial
Please see the Jupyter notebook in the **Tutorial** folder. It includes several tutorials, providing examples across different species, sequencing technologies, and diseases.

## License
This project is covered under the **MIT License**.

