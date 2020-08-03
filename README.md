# GraphData

TODO: add reference
+ Cora

+ Citeseer

+ Cora_ml

+ Polblogs

+ Pubmed

# Usage
Each directory contain 3 files, denoting:
+ `adjacency matrix` (not symmetric): Scipy CSR matrix
+ `feature matrix`: Numpy array
+ `node labels`: Numpy array

```python
import pickle

# Your path to the dataset, here is `Cora` dataset
base_path = "GraphData/cora"

with open(f"{base_path}/adj.pkl", 'rb') as f:
    adj = pickle.load(f)
    
features = np.load(f"{base_path}/feature.npy")
label = np.load(f"{base_path}/label.npy")
```