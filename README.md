# GraphData


## Planetoid datasets: CORA, CiteSeer and PubMed

citation network datasets in https://github.com/kimiyoung/planetoid

nodes are documents and edges are citation links. Label rate denotes the number of labeled nodes that are used for training divided by the total number of nodes in each dataset. 

```tex
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

## Amazon Computers and Amazon Photo

Amazon Computers and Amazon Photo are segments of the Amazon co-purchase graph,where nodes represent goods, edges indicate that two goods are frequently bought together, node features are bag-of-words encoded product reviews, and class labels are given by the product category. 

```tex
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



## Coauthor CS and Coauthor Physics

Coauthor CS and Coauthor Physics are co-authorship graphs based on the Microsoft Academic Graph from the KDD Cup 2016 challenge. Here, nodes are authors, that are connected by an edge if they co-authored a paper; node features represent paper keywords for each author’s papers, and class labels indicate most active fields of study for each author.

```
https://kddcup2016.azurewebsites.net/
```



The above datasets are collected from

https://github.com/shchur/gnn-benchmark

```tex
@article{shchur2018pitfalls,
  title={Pitfalls of Graph Neural Network Evaluation},
  author={Shchur, Oleksandr and Mumme, Maximilian and Bojchevski, Aleksandar and G{\"u}nnemann, Stephan},
  journal={Relational Representation Learning Workshop, NeurIPS 2018},
  year={2018}
}
```

---

## DBLP

```tex
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

## CiteSeer_Full

```tex
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

## CORA_Full and CORA-ML

CORA_Full, citation network dataset, an extended version of CORA

CORA-ML, extracted from the original data the entire network of CORA

```tex
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

```tex
@inproceedings{bojchevski2018deep,
title={Deep Gaussian Embedding of Graphs:  Unsupervised Inductive Learning via Ranking},
author={Aleksandar Bojchevski and Stephan Günnemann},
booktitle={International Conference on Learning Representations},
year={2018},
url={https://openreview.net/forum?id=r1ZdKJ-0W},
}
```

---

## Reddit

http://snap.stanford.edu/graphsage/

```tex
 @inproceedings{hamilton2017inductive,
     author = {Hamilton, William L. and Ying, Rex and Leskovec, Jure},
     title = {Inductive Representation Learning on Large Graphs},
     booktitle = {NIPS},
     year = {2017}
   }
```

## NELL

https://github.com/kimiyoung/planetoid

```tex
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

```tex
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

## Flickr and BlogCatalog

BlogCatalog : It is a dataset of a blog community social network, which contains 5,196 users as nodes, 171,743 edges indicating the user interactions, and 8,189 attribute categories denoting the keywords of their blogs. Users could register their blogs into six different predefined classes, which are set as labels. 

Flickr: It is a benchmark attributed social network dataset containing 7,575 nodes. Each node is a Flickr user and each attribute category is a tag related to the photos shared by users. There are 239,738 undirected edges in this network, which indicate the following relationships among users. The nine groups that users have joined are considered as target labels.

```tex
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

```tex
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