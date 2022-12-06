## 1- Notions de base 

**Pourquoi Pyspark ?**

Les commandes spécifiques de Spark s’exécutent en Java, Scala et aussi pour certaines en Python. D’où 
l’intérêt de l’apprentissage de Python qui permet sans "trop" d’effort de franchir le changement d’échelle 
en volume, notamment par l’emploi de la librairie ou plutôt de l’interface de programmation (Application 
Interface programmation ou API) dédiée PySpark ; cette API propose une utilisation interactive et même 
celle des calepins d’IPython. 
Spark intègre deux principales librairies :

– **SQL** pour du requêtage dans des données volumineuses et structurées, 

– **MLlib** avec les principaux algorithmes d’apprentissage et méthodes statistique.

**Configuration**

L’environnement utilisé est décrit par la commande SparkContext initialisant un objet SparkConf qui 
définit la configuration utilisée comme par exemple l’URL du nœud "maître" (driver) du cluster de calcul 
utilisé, le nombre de nœuds "esclaves" ou workers, leur espace mémoire réservé à chacun dans le cas de 
machines virtuelles.
Cet environnement est prédéfini à l’installation de Spark.

**Resilient Distributed Dataset (RDD)**

La notion de table de données résiliente est au cœur des fonctionnalités de Spark. Il s’agit d’un ensemble 
d’enregistrement ou objets d’un type spécifique, partitionnés ou distribués sur plusieurs nœuds du cluster. 
Cet objet est tolérant aux pannes, si un nœud est touché par une défaillance matérielle ou de réseau, la 
table résiliente est reconstruite automatiquement sur les autres nœuds et la tâche achevée. Les opérations 
sur les RDD se déclinent "normalement" pour des données distribuées en étapes Map et Reduce. La 
principale propriété des RDD de Spark est la possibilité de les cacher en mémoire (RAM) de chaque nœud. 
C’est ce qui permet d’économiser énormément d’accès disques qui sont le principal verrou, en termes de
temps de calcul, lors de l’exécution d’algorithmes itératifs.

## 2-Présentation de MLLib 
### Fonctionnalités
Cette librairie est en plein développement ; seule la documentation en ligne de la dernière version est à 
jour concernant la liste des méthodes disponibles. Voici un rapide aperçu de MLlib :

- Statistique de base : Univariée, corrélation, échantillonnage stratifié, tests d’hypothèse, 
générateurs aléatoires, transformation (standardisation, quantification de textes avec TF-IDF et 
vectorisation), sélection (chi2) de variables (features).

- Exploration multidimensionnelle Classification non-supervisée (k-means avec version en 
ligne, modèles de mélanges gaussiens, LDA ou Latent Derichlet Allocation, réduction de dimension 
(SVD et ACP mais en java ou scala pas en python), factorisation non négative (NMF) par moindres 
carrés alternés (ALS). 

- Apprentissage Méthodes linéaires : SVM, régression gaussienne et binomiale ou logistique avec 
pénalisation L1 ou L2 ; estimation par gradient stochastique, ou L-BFGS ; classifieur bayésien naïf, 
arbre de décision, forêts aléatoires, boosting (gradient boosting machine).

### Type de données 
**LabeledPoint** : Ce type est spécifique aux algorithmes d’apprentissage et associe un "label", en fait un réel, et un vecteur. 
Ce "label" est soit la valeur de la variable Y quantitative à modéliser en régression, soit un code de classe : 
0.0, 1.0... en classification supervisée ou discrimination.

**Rating** :Type de données (note d’un article par un client) spécifique aux systèmes de recommandation et donc à 
l’algorithme de factorisation (ALS) disponible. 

**Model** : La classe Model est le résultat d’un algorithme d’apprentissage qui dispose de la fonction predict() pour 
appliquer le modèle à une nouvelle observation ou à une table de données résiliente de nouvelles 
observations

## 3- Partie Pratique
### **Avoir une première idée sur la perfomance des modèles obtenue avant tout traitement**
![image](https://user-images.githubusercontent.com/77699359/205884693-3c8763f5-0262-457e-aaf2-fda68f4936cc.png)

### **Objectif ?**

Optimiser la performance des modèles

### **Approches utilisées**

Les 3 approches sur lesquels je me suis basée afin de faire augmenter la 
performance des 2 modèles :
1. Feature selection using Pearson correlation
2. Reduction dimensionnelle using PCA
3. Traitement de langage naturel – NLP

### **Best accuracy obtained so far**
![image](https://user-images.githubusercontent.com/77699359/205884828-d1cff16f-9352-4f23-8d4e-b00d12af71c6.png)






