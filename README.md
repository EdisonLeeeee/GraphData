# GraphData

TODO: add reference
+ Cora

+ Citeseer

+ Cora_ml

+ Polblogs

+ Pubmed

# Usage
Each ZIP file contains 3 files:
+ adj.pkl: `adjacency matrix` (not symmetric), Scipy CSR matrix
+ feature.npy: `feature matrix`, Numpy array
+ label.npy: `node labels`, Numpy array

```python
import numpy as np
import zipfile
# Your path to the dataset, here is `Cora` dataset
base_path = "GraphData/datasets"

with zipfile.ZipFile(f'{base_path}/cora.zip', 'r') as zipf:
    zipf.extractall(f'{base_path}/')
    
with open(f"{base_path}/adj.pkl", 'rb') as f:
    adj = np.load(f, allow_pickle=True)
    
features = np.load(f"{base_path}/feature.npy")
label = np.load(f"{base_path}/label.npy")
```