# P6-OC-DataScientist

## Projet : Classifiez automatiquement des biens de consommation
Projet 6 de la formation OpenClassrooms du parcours data scientist

## Objectifs du projet
L’entreprise « Place de marché » souhaite lancer une marketplace e-commerce. 
Sur la place de marché, des vendeurs proposent des articles à des acheteurs en postant une photo et une description.

Aujourd’hui, l’attribution de la catégorie d’un article est faite manuellement par les vendeurs et le volume des articles est petit. 

Pour rendre l’expérience utilisateur des vendeurs (faciliter la mise en ligne de nouveaux articles) et des acheteurs (faciliter la recherche de produits) la plus fluide possible, et dans l'optique d'un passage à l'échelle, il devient nécessaire d'automatiser cette tâche

Etant Data Scientist dans l'entreprise, mon rôle est d'étudier la faisabilité d'un moteur de classification des articles en différentes catégories, avec un niveau de précision suffisant.


### Données à disposition 

Deux types de données :
- Visuelles : une base de données contenant une image par produit
- Textuelles : un jeu de données sur 1050 produits avec 15 variables descriptives :
  - Image : nom de l’image dans la base de données
  - product_name : nom du produit en anglais 
  - product_category_tree  : l’arborescence complète d’un article : 1er niveau de sous catégories = 7 catégories
  - Description : description du produit en anglais
  - Et d’autres variables non utilisées : uniq_id, crawl_timestamp, product_url, pid, retail_price, discounted_price, is_FK_Advantage_product, product_rating, overall_rating, brand, product_specifications

### Missions 

#### Réaliser une étude de faisabilité d'un moteur de classification d'articles, basé sur une image et une description, pour l'automatisation de l'attribution de la catégorie de l'article. 

Je dois analyser les descriptions textuelles et les images des produits, au travers des étapes suivantes : 
- Un prétraitement des données texte ou image suivant le cas ;
- Une extraction de features ;
- Une réduction en 2 dimensions, afin de projeter les produits sur un graphique 2D, sous la forme de points dont la couleur correspondra à la catégorie réelle ;
- Analyse du graphique afin d’en déduire ou pas, à l’aide des descriptions ou des images, la faisabilité de regrouper automatiquement des produits de même catégorie ;
- Réalisation d’une mesure pour confirmer ton analyse visuelle, en calculant la similarité entre les catégories réelles et les catégories issues d’une segmentation en clusters.
  
Il faut que je démontre, par cette approche, la faisabilité de regrouper automatiquement des produits de même catégorie.
Afin d’extraire les features texte, il sera nécessaire de mettre en œuvre : 
- deux approches de type “bag-of-words”, comptage simple de mots et Tf-idf ;
- une approche de type word/sentence embedding classique avec Word2Vec (ou Glove ou FastText) ;
- une approche de type word/sentence embedding avec BERT ;
- une approche de type word/sentence embedding avec USE (Universal Sentence Encoder). 
En pièce jointe, tu trouveras un exemple de mise en œuvre de ces approches d’extraction de features texte sur un autre dataset. Je t’invite à l’utiliser comme point de départ, cela va te faire gagner beaucoup de temps !
Afin d’extraire les features image, il sera nécessaire de mettre en œuvre :
- un algorithme de type SIFT / ORB / SURF ;
- un algorithme de type CNN Transfer Learning.

#### Réaliser une classification supervisée à partir des images avec une data augmentation pour optimiser le modèle

Je dois réaliser une classification supervisée à partir des images puis mettre en place une data augmentation afin d’optimiser le modèle.
Un exemple de mise en œuvre de classification supervisée sur un autre dataset est mis à disposition est à utiliser en point de départ pour gagner du temps.

#### Tester
L'entreprise souhaite élargir sa gamme de produits, en particulier dans l’épicerie fine. 
Je dois donc tester la collecte de produits à base de “champagne” via l’API (RapidAPI).
Je dois fournir une extraction des 10 premiers produits dans un fichier “.csv”, contenant pour chaque produit les données suivantes : foodId, label, category, foodContentsLabel, image.


## Compétences évaluées
- Utiliser des techniques d’augmentation des données
- Prétraiter des données texte pour obtenir un jeu de données exploitable
- Représenter graphiquement des données à grandes dimensions
- Prétraiter des données image pour obtenir un jeu de données exploitable
- Mettre en œuvre des techniques de réduction de dimension
- Définir la stratégie de collecte de données en recensant les API disponibles
- Définir la stratégie d’élaboration d’un modèle d'apprentissage profond
- Évaluer la performance des modèles d’apprentissage profond selon différents critères

## Découpage des dossiers

- Saubot_Julie_1_notebook_pretraitement_feature_extraction_faisaibilite_072023.ipynb : notebook contenant les fonctions permettant le prétraitement et la feature extraction des données textes et images ainsi que les résultats de l’étude de faisabilité (graphiques, mesure de similarité)
- Saubot_Julie_2_notebook_classification_072023.ipynb : notebook de classification supervisée des images
- Saubot_Julie_3_notebook_traitement_avec_technique_recente_072023.ipynb : notebook de classification supervisée des images avec technique récente 
- Saubot_Julie_4_script_Python_072023.ipynb : script Python de test de l’API
- Saubot_Julie_5_presentation_072023.pptx : support de présentation pour la soutenance
  
## Lien utiles

- Données utilisées : https://s3-eu-west-1.amazonaws.com/static.oc-static.com/prod/courses/files/Parcours_data_scientist/Projet+-+Textimage+DAS+V2/Dataset+projet+prétraitement+textes+images.zip
- Notebook d'exemple d'étude de faisabilité : https://s3.eu-west-1.amazonaws.com/course.oc-static.com/projects/Data_Scientist_P6/Weather_Images_CNN_Transfer_Learning_Stage_1_feasibility_V1.0.ipynb
- Notebook d'exemple de classification supervisée d'images : https://s3.eu-west-1.amazonaws.com/course.oc-static.com/projects/Data_Scientist_P6/Weather_Images_CNN_Transfer_Learning_Stage_2_supervised_classification_V1.0.ipynb
- API : https://rapidapi.com/edamam/api/edamam-food-and-grocery-database
