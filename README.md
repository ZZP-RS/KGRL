## Introduction
KGRL focuses on long tail recommendations by utilizing KG-enhanced representation learning.

## Author
Yao Zhang; Zhipeng Zhang; Mingwei Wang; Xiujun Zhao; Shu Li; Wenchao Zhang

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
We provided three datasets to validate KGRL: MovieLens-1M, Last-FM, and Amazon-book.

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
