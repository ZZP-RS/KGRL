## Introduction
KGRL is a niche KG-enhanced Representation Learning for long tail recommendations. KGRL mainly contains the components as follows: 1) Long-tail interest representation learning on the user side. This module leverages semantic-based correlations in KG to make the long-tail neighbors selection for the target user, and utilizes a hybrid attention network to aggregate the features of both long-tail neighbors and original neighbors into the embeddings of the target user. 2) Co-occurrence representation learning on the item side. This module makes co-occurrence neighbor selection to extract the co-occurrence neighbors for long-tail items, and further employs a hybrid attention network to aggregate the features of both co-occurrence neighbors and original neighbors into the embeddings of long-tail items. 3) Model prediction and multi-task optimization. This module employs layer-aggregation to concatenate embeddings from each step into a single vector, and utilizes a multi-task training strategy to train the parameters of KGRL until optimal.

## Author
Yao Zhang; Zhipeng Zhang; Mingwei Wang; Xiujun Zhao; Shu Li; Wenchao Zhang
{School of Mechanical Engineering and Automation, Dalian Polytechnic University, Dalian, China}
{School of Computer Science and Artificial Intelligence, Liaoning Normal University, Dalian, China}

## Environment Requirement
The code has been tested running under Python 3.7.10. The required packages are as follows:
* torch == 1.8.0
* numpy == 1.23.5
* pandas == 1.5.3
* scipy == 1.10.1
* tqdm == 4.65.0
* scikit-learn == 1.2.2

## KGRL operation steps
1. run selector.py to conduct the long-tail interest representation learning process on the user side
~~~
python selector.py
~~~
2. run doCooccur.py to construct the co-occurrence representation learning process on the item side
~~~
python doCooccur.py
~~~
3. start KGRL
~~~
python main_KGRL.py
~~~


## datasets
We provided three datasets to validate KGRL: MovieLens-1M, Last-FM, and Amazon-book. The following table shows the information of three datasets:

|                | Last-FM |MovieLens-1M| Amazon-book |
| :------------: | :-----: |  :-----:   |:-----:   |
|    n_users     |  23566  |    6040    | 70679 |
|    n_items     |  48123  |    3655    |24915|
| n_interactions | 3034796 |   997579   |847733|
|   n_entities   | 58266  |   398505   | 88572|
|  n_relations   |    9    |     57     | 39|
|   n_triples    | 464567  |   3396595  |2557746|

Besides the user-item interactions, we need to construct item knowledge for each dataset. We mapped items of three datasets to Freebase entities to construct KG.
The following table shows the KG information of three datasets:

| Knowledge Graph |   Freebase(Last-FM)   |  Freebase(MovieLens-1M)  | Freebase(Amazon-book)
|:---------------:|          :-----------:         |     :-------:     |:-------:     |
|   #entities    |              58266            |       398505      |88572|
|   #relations   |                 9              |         57        |39|
|    #triples    |              464567            |       3396595     |2557746|
