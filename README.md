## Introduction
KGRL focuses on long tail recommendations by utilizing KG-enhanced representation learning.


## Environment Requirement
```
The code has been tested running under Python 3.7.10. The required packages are as follows:

torch == 1.8.0
numpy == 1.23.5
pandas == 1.5.3
scipy == 1.10.1
tqdm == 4.65.0
scikit-learn == 1.2.2
```

## KGRL operation steps
1. run doCooccur.py to generate co-occurrence Neighbors
```
python doCooccur.py
```
2. run selector.py to generate Long-tail Neighbors
```
python selector.py
```
3. start KGRL
```
python main_KGRL.py
```

## Datasets
We provided three datasets to validate KGRL: MovieLens-1M, Last-FM, Amazon-book, and Yelp2018.

|                | Last-FM |MovieLens-1M| Amazon-book | Yelp2018 |
| :------------: | :-----: |  :-----:   |:-----:   |:-----:   |
|    n_users     |  23566  |    6040    | 70679 | 45919 |
|    n_items     |  48123  |    3655    |24915| 45538 |
| n_interactions | 3034796 |   997579   |847733| 1185068 |
|   n_entities   | 58266  |   398505   | 88572| 90961 |
|  n_relations   |    9    |     57     | 39|42|
|   n_triples    | 464567  |   3396595  |2557746| 1853704|

Besides the user-item interactions, we need to construct item knowledge for each dataset. We mapped items of three datasets to Freebase entities to construct KG.
The following table shows the KG information of three datasets:

| Knowledge Graph |   Freebase(Last-FM)   |  Freebase(MovieLens-1M)  | Freebase(Amazon-book) | Freebase(Yelp2018) 
|:---------------:|          :-----------:         |     :-------:     |:-------:     |
|   #entities    |              58266            |       398505      |88572|90961|
|   #relations   |                 9              |         57        |39|42|
|    #triples    |              464567            |       3396595     |2557746|1853704|
