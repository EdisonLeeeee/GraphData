# GraphData
- [GraphData](#graphdata)
  - [Glance of graphs](#glance-of-graphs)
  - [Single Graph](#single-graph)
    - [Planetoid datasets: CORA, CiteSeer and PubMed](#planetoid-datasets-cora-citeseer-and-pubmed)
    - [Amazon Computers and Amazon Photo](#amazon-computers-and-amazon-photo)
    - [Coauthor CS and Coauthor Physics](#coauthor-cs-and-coauthor-physics)
    - [DBLP](#dblp)
    - [CiteSeer_Full](#citeseer_full)
    - [CORA_Full and CORA-ML](#cora_full-and-cora-ml)
    - [Reddit](#reddit)
      - [Source-SNAP](#source-snap)
      - [Source-DGL](#source-dgl)
      - [Source-TUM](#source-tum)
    - [NELL](#nell)
    - [Flickr and BlogCatalog](#flickr-and-blogcatalog)
    - [KDD Cup 2020](#kdd-cup-2020)
    - [UAI2010](#uai2010)
    - [ACM](#acm)
    - [MAG-Scholar](#mag-scholar)
    - [Karateclub Datasets](#karateclub-datasets)
      - [Node-level](#node-level)
      - [Graph-level](#graph-level)

# Usage of `.npz` datasets
```python
import os.path as osp
import numpy as np

def load_npz(filepath):
    filepath = osp.abspath(osp.expanduser(filepath))

    if not filepath.endswith('.npz'):
        filepath = filepath + '.npz'
    if osp.isfile(filepath):
        with np.load(filepath, allow_pickle=True) as loader:
            loader = dict(loader)
            for k, v in loader.items():
                if v.dtype.kind in {'O', 'U'}:
                    loader[k] = v.tolist()
            return loader
    else:
        raise ValueError(f"{filepath} doesn't exist.")
```
e.g., run load_npz('cora') and it returns a dict instance `loader`, it might have the following `keys`:
+ `adj_matrix`: scipy.sparse.csr_matrix, adjacency matrix. NOTE: the adjacency matrix might not be symmetric.
+ `node_attr`: scipy.sparse.csr_matrix or numpy.ndarray, node attribute matrix
+ `node_label`: scipy.sparse.csr_matrix or numpy.ndarray, node labels
+ `metadata`: dict, additional metadata such as text.

## Glance of graphs

|name|num_nodes|num_edges|num_attrs|num_graphs|is_directed|
|:---:|:---:|:---:|:---:|:---:|:---:|
|karate_club|34|78|0|6.7474%|0|
|polblogs|1,490|19,025|0|0.8569%|1|
|cora|2,708|5,429|1,433|0.0740%|1|
|cora_ml|2,995|8,416|2,879|0.0938%|1|
|acm|3,025|13,128|1,870|0.1435%|0|
|uai|3,067|28,314|4,973|0.3010%|0|
|citeseer|3,312|4,715|3,703|0.0430%|1|
|citeseer_full|4,230|5,358|602|0.0299%|1|
|blogcatalog|5,196|171,743|8,189|0.6361%|0|
|flickr|7,575|239,738|12,047|0.4178%|0|
|amazon_photo|7,650|143,663|745|0.2455%|1|
|amazon_cs|13,752|287,209|767|0.1519%|1|
|dblp|17,716|52,867|1,639|0.0168%|0|
|coauthor_cs|18,333|81,894|6,805|0.0244%|0|
|pubmed|19,717|44,324|500|0.0114%|0|
|cora_full|19,793|65,311|8,710|0.0167%|1|
|coauthor_phy|34,493|247,962|8,415|0.0208%|0|

## Single Graph
### Planetoid datasets: CORA, CiteSeer and PubMed

citation network datasets in https://github.com/kimiyoung/planetoid

nodes are documents and edges are citation links. Label rate denotes the number of labeled nodes that are used for training divided by the total number of nodes in each dataset. 

```bibtex
@article{SenNBGGE08,
  author    = {Prithviraj Sen and
               Galileo Namata and
               Mustafa Bilgic and
               Lise Getoor and
               Brian Gallagher and
               Tina Eliassi{-}Rad},
  title     = {Collective Classification in Network Data},
  journal   = {{AI} Mag.},
  volume    = {29},
  number    = {3},
  pages     = {93--106},
  year      = {2008}
}
```

### Amazon Computers and Amazon Photo

Amazon Computers and Amazon Photo are segments of the Amazon co-purchase graph,where nodes represent goods, edges indicate that two goods are frequently bought together, node features are bag-of-words encoded product reviews, and class labels are given by the product category. 

```bibtex
@inproceedings{McAuleyTSH15,
  author    = {Julian J. McAuley and
               Christopher Targett and
               Qinfeng Shi and
               Anton van den Hengel},
  editor    = {Ricardo Baeza{-}Yates and
               Mounia Lalmas and
               Alistair Moffat and
               Berthier A. Ribeiro{-}Neto},
  title     = {Image-Based Recommendations on Styles and Substitutes},
  booktitle = {Proceedings of the 38th International {ACM} {SIGIR} Conference on
               Research and Development in Information Retrieval, Santiago, Chile,
               August 9-13, 2015},
  pages     = {43--52},
  publisher = {{ACM}},
  year      = {2015}
}
```



### Coauthor CS and Coauthor Physics

Coauthor CS and Coauthor Physics are co-authorship graphs based on the Microsoft Academic Graph from the KDD Cup 2016 challenge. Here, nodes are authors, that are connected by an edge if they co-authored a paper; node features represent paper keywords for each author’s papers, and class labels indicate most active fields of study for each author.

```
https://kddcup2016.azurewebsites.net/
```



The above datasets are collected from

https://github.com/shchur/gnn-benchmark

```bibtex
@article{shchur2018pitfalls,
  title={Pitfalls of Graph Neural Network Evaluation},
  author={Shchur, Oleksandr and Mumme, Maximilian and Bojchevski, Aleksandar and G{\"u}nnemann, Stephan},
  journal={Relational Representation Learning Workshop, NeurIPS 2018},
  year={2018}
}
```

---

### DBLP

```bibtex
@inproceedings{PanWZZW16,
  author    = {Shirui Pan and
               Jia Wu and
               Xingquan Zhu and
               Chengqi Zhang and
               Yang Wang},
  editor    = {Subbarao Kambhampati},
  title     = {Tri-Party Deep Network Representation},
  booktitle = {Proceedings of the Twenty-Fifth International Joint Conference on
               Artificial Intelligence, {IJCAI} 2016, New York, NY, USA, 9-15 July
               2016},
  pages     = {1895--1901},
  publisher = {{IJCAI/AAAI} Press},
  year      = {2016}
}
```

### CiteSeer_Full

```bibtex
@inproceedings{GilesBL98,
  author    = {C. Lee Giles and
               Kurt D. Bollacker and
               Steve Lawrence},
  title     = {CiteSeer: An Automatic Citation Indexing System},
  booktitle = {Proceedings of the 3rd {ACM} International Conference on Digital Libraries,
               June 23-26, 1998, Pittsburgh, PA, {USA}},
  pages     = {89--98},
  publisher = {{ACM}},
  year      = {1998}
}
```

### CORA_Full and CORA-ML

CORA_Full, citation network dataset, an extended version of CORA

CORA-ML, extracted from the original data the entire network of CORA

```bibtex
@article{McCallumNRS00,
  author    = {Andrew McCallum and
               Kamal Nigam and
               Jason Rennie and
               Kristie Seymore},
  title     = {Automating the Construction of Internet Portals with Machine Learning},
  journal   = {Inf. Retr.},
  volume    = {3},
  number    = {2},
  pages     = {127--163},
  year      = {2000}
}
```



The above datasets are collected from

https://github.com/abojchevski/graph2gauss

```bibtex
@inproceedings{bojchevski2018deep,
title={Deep Gaussian Embedding of Graphs:  Unsupervised Inductive Learning via Ranking},
author={Aleksandar Bojchevski and Stephan Günnemann},
booktitle={International Conference on Learning Representations},
year={2018},
url={https://openreview.net/forum?id=r1ZdKJ-0W},
}
```

---

### Reddit
233K nodes, 11.6M edges, 602 node features
#### Source-SNAP
Link: http://snap.stanford.edu/graphsage/

```bibtex
 @inproceedings{hamilton2017inductive,
     author = {Hamilton, William L. and Ying, Rex and Leskovec, Jure},
     title = {Inductive Representation Learning on Large Graphs},
     booktitle = {NIPS},
     year = {2017}
   }
```
#### Source-DGL
Link: https://data.dgl.ai/dataset/reddit.zip

#### Source-TUM
Link: https://ndownloader.figshare.com/files/23742119

### NELL

https://github.com/kimiyoung/planetoid

```bibtex
@inproceedings{CarlsonBKSHM10,
  author    = {Andrew Carlson and
               Justin Betteridge and
               Bryan Kisiel and
               Burr Settles and
               Estevam R. Hruschka Jr. and
               Tom M. Mitchell},
  editor    = {Maria Fox and
               David Poole},
  title     = {Toward an Architecture for Never-Ending Language Learning},
  booktitle = {Proceedings of the Twenty-Fourth {AAAI} Conference on Artificial Intelligence,
               {AAAI} 2010, Atlanta, Georgia, USA, July 11-15, 2010},
  publisher = {{AAAI} Press},
  year      = {2010}
```

```bibtex
@inproceedings{DBLP:conf/icml/YangCS16,
  author    = {Zhilin Yang and
               William W. Cohen and
               Ruslan Salakhutdinov},
  editor    = {Maria{-}Florina Balcan and
               Kilian Q. Weinberger},
  title     = {Revisiting Semi-Supervised Learning with Graph Embeddings},
  booktitle = {Proceedings of the 33nd International Conference on Machine Learning,
               {ICML} 2016, New York City, NY, USA, June 19-24, 2016},
  series    = {{JMLR} Workshop and Conference Proceedings},
  volume    = {48},
  pages     = {40--48},
  publisher = {JMLR.org},
  year      = {2016}
}
```

### Flickr and BlogCatalog

BlogCatalog : It is a dataset of a blog community social network, which contains 5,196 users as nodes, 171,743 edges indicating the user interactions, and 8,189 attribute categories denoting the keywords of their blogs. Users could register their blogs into six different predefined classes, which are set as labels. 

Flickr: It is a benchmark attributed social network dataset containing 7,575 nodes. Each node is a Flickr user and each attribute category is a tag related to the photos shared by users. There are 239,738 undirected edges in this network, which indicate the following relationships among users. The nine groups that users have joined are considered as target labels.

```bibtex
@inproceedings{LiHTL15,
  author    = {Jundong Li and
               Xia Hu and
               Jiliang Tang and
               Huan Liu},
  editor    = {James Bailey and
               Alistair Moffat and
               Charu C. Aggarwal and
               Maarten de Rijke and
               Ravi Kumar and
               Vanessa Murdock and
               Timos K. Sellis and
               Jeffrey Xu Yu},
  title     = {Unsupervised Streaming Feature Selection in Social Media},
  booktitle = {Proceedings of the 24th {ACM} International Conference on Information
               and Knowledge Management, {CIKM} 2015, Melbourne, VIC, Australia,
               October 19 - 23, 2015},
  pages     = {1041--1050},
  publisher = {{ACM}},
  year      = {2015}
}
```

both datasets are collected form

https://github.com/xhuang31/LANE

```bibtex
@inproceedings{HuangLH17,
  author    = {Xiao Huang and
               Jundong Li and
               Xia Hu},
  editor    = {Maarten de Rijke and
               Milad Shokouhi and
               Andrew Tomkins and
               Min Zhang},
  title     = {Label Informed Attributed Network Embedding},
  booktitle = {Proceedings of the Tenth {ACM} International Conference on Web Search
               and Data Mining, {WSDM} 2017, Cambridge, United Kingdom, February
               6-10, 2017},
  pages     = {731--739},
  publisher = {{ACM}},
  year      = {2017}
}
```

### KDD Cup 2020
+ KDDS1
https://www.biendata.xyz/competition/kddcup_2020/data/

+ KDDS2
https://www.biendata.xyz/competition/kddcup_2020_formal/data/
the label of the last 50,000 test nodes are released at https://github.com/THUDM/GIAAD

### UAI2010
Link: https://github.com/zhumeiqiBUPT/AM-GCN

```bibtex
@inproceedings{wang2018unified,
  title={A Unified Weakly Supervised Framework for Community Detection and Semantic Matching},
  author={Wang, Wenjun and Liu, Xiao and Jiao, Pengfei and Chen, Xue and Jin, Di},
  booktitle={Pacific-Asia Conference on Knowledge Discovery and Data Mining},
  pages={218--230},
  year={2018},
  organization={Springer}
}
```
### ACM
This network is extracted from ACM dataset where nodes represent papers and there is an edge between two papers if they have the same author. All the papers are divided into 3 classes (Database, Wireless Communication, DataMining). The features are the bag-of-words representa- tions of paper keywords.

Link1: https://github.com/Jhy1993/HAN
Cite: 
```bibtex
@article{han2019,
title={Heterogeneous Graph Attention Network},
author={Xiao, Wang and Houye, Ji and Chuan, Shi and  Bai, Wang and Peng, Cui and P. , Yu and Yanfang, Ye},
journal={WWW},
year={2019}
}
```
Link2: https://github.com/zhumeiqiBUPT/AM-GCN
Cite: 
```bibtex
@inproceedings{DBLP:conf/kdd/0017ZB0SP20,
  author    = {Xiao Wang and
               Meiqi Zhu and
               Deyu Bo and
               Peng Cui and
               Chuan Shi and
               Jian Pei},
  title     = {{AM-GCN:} Adaptive Multi-channel Graph Convolutional Networks},
  booktitle = {{KDD} '20: The 26th {ACM} {SIGKDD} Conference on Knowledge Discovery
               and Data Mining, Virtual Event, CA, USA, August 23-27, 2020},
  pages     = {1243--1253},
  publisher = {{ACM}},
  year      = {2020},
}
```
### MAG-Scholar
a new benchmark dataset based on the Microsoft Academic Graph (MAG). Nodes represent papers, edges denote
citations, and node features correspond to a bag-of-words representation of paper abstracts. The graph is augmented with "groundtruth" node labels corresponding to the papers’ field of study.

Link: https://figshare.com/articles/dataset/mag_scholar/12696653
Cite: 
```bibtex
@inproceedings{bojchevski2020pprgo,
  title={Scaling Graph Neural Networks with Approximate PageRank},
  author={Bojchevski, Aleksandar and Klicpera, Johannes and Perozzi, Bryan and Kapoor, Amol and Blais, Martin and R{\'o}zemberczki, Benedek and Lukasik, Michal and G{\"u}nnemann, Stephan},
  booktitle = {Proceedings of the 26th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining},
  year={2020},
  publisher = {ACM},
  address = {New York, NY, USA},
}
```
### Karateclub Datasets
Datasets from [Karateclub](https://github.com/benedekrozemberczki/karateclub)
#### Node-level
+ deezer
+ facebook
+ github
+ lastfm
+ twitch
+ wikipedia
  
#### Graph-level
+ reddit10k

Cite:
```bibtex
@inproceedings{karateclub,
       title = {{Karate Club: An API Oriented Open-source Python Framework for Unsupervised Learning on Graphs}},
       author = {Benedek Rozemberczki and Oliver Kiss and Rik Sarkar},
       year = {2020},
       pages = {3125–3132},
       booktitle = {Proceedings of the 29th ACM International Conference on Information and Knowledge Management (CIKM '20)},
       organization = {ACM},
}
```

### FB15k
FB15K_URL = "https://dl.fbaipublicfiles.com/starspace/fb15k.tgz"
FILENAMES = [
    "FB15k/freebase_mtr100_mte100-train.txt",
    "FB15k/freebase_mtr100_mte100-valid.txt",
    "FB15k/freebase_mtr100_mte100-test.txt",
]

### MUSAE
Datasets from [MUSAE](https://github.com/benedekrozemberczki/MUSAE)
╒═══════════╤═══════════════════════════════════════════════════════════════════╕
│ Names     │ Description                                                           │
╞═══════════╪═══════════════════════════════════════════════════════════════════╡
│ chameleon │ Wiki-chameleon dataset (classification)                           │
├───────────┼───────────────────────────────────────────────────────────────────┤
│ crocodile │ Wiki-crocodile dataset (classification)                           │
├───────────┼───────────────────────────────────────────────────────────────────┤
│ squirrel  │ Wiki-squirrel dataset (node classification)                       │
├───────────┼───────────────────────────────────────────────────────────────────┤
│ facebook  │ facebook dataset (classification)                                 │
├───────────┼───────────────────────────────────────────────────────────────────┤
│ github    │ github dataset, the same as KarateClub('github') (classification) │
├───────────┼───────────────────────────────────────────────────────────────────┤
│ DE        │ Twitch-DE dataset (classification, regression)                    │
├───────────┼───────────────────────────────────────────────────────────────────┤
│ ENGB      │ Twitch-ENGB dataset (classification, regression)                  │
├───────────┼───────────────────────────────────────────────────────────────────┤
│ ES        │ Twitch-ES dataset (classification, regression)                    │
├───────────┼───────────────────────────────────────────────────────────────────┤
│ FR        │ Twitch-FR dataset (classification, regression)                    │
├───────────┼───────────────────────────────────────────────────────────────────┤
│ PTBR      │ Twitch-PTBR dataset (classification, regression)                  │
├───────────┼───────────────────────────────────────────────────────────────────┤
│ RU        │ Twitch-RU dataset (classification, regression)                    │
├───────────┼───────────────────────────────────────────────────────────────────┤
│ ZHTW      │ Twitch-ZHTW dataset (classification, regression)                  │
╘═══════════╧═══════════════════════════════════════════════════════════════════╛
Cite
```bibtex
@misc{rozemberczki2019multiscale,    
       title = {{Multi-scale Attributed Node Embedding}},   
       author = {Benedek Rozemberczki and Carl Allen and Rik Sarkar},   
       year = {2019},   
       eprint = {1909.13021},  
       archivePrefix = {arXiv},  
       primaryClass = {cs.LG}   
       }
```

### PDN
Synthetic node classification dataset from PDN: https://github.com/benedekrozemberczki/PDN
Cite
```bibtex
@inproceedings{rozemberczki2021pdn,    
                title={{Pathfinder Discovery Networks for Neural Message Passing}},    
                author={Benedek Rozemberczki and Peter Englert and Amol Kapoor and Martin Blais and Bryan Perozzi},    
                booktitle = {Proceedings of The Web Conference 2021},
                year={2021},    
                organization={ACM}    
                }
```