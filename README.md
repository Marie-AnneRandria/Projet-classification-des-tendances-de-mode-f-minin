# Classification des Tendances dans le secteur de la mode féminine
 
## Contexte
Dans ce projet, je développe un modèle de classification supervisée visant à prédire si un vêtement sera recommandé par les clients, à partir de leurs avis textuels et des caractéristiques du produit.

---

## Problématique
Peut-on prédire, à partir des caractéristiques d'un produit et du contenu textuel des avis clients, si un produit sera recommandé ou non ?

---

## Jeu de donnée utilisé
** Women's E-Commerce Clothing Reviews** -[Kaggle] (https://www.kaggle.com/datasets/nicapotato/womens-ecommerce-clothing-reviews)

- Ce jeu de donnée contient 23 486 observations et 10 variables.
-  Variable cible: `Recommended IND` (0 = Non recommandé, 1 = Recommandé)

---

## Méthodologie du projet

### 1. Nettoyage des données
- Suppresion des valeurs manquantes (`title`, `review`, `department`, `division`, `class`)
- Renommage et normalisation des colonnes

### 2. Analyse exploratoire (EDA)
- Distribution des divisions, départements et des notes (rating)
- Taux de recommandation: **81.8%** des produits sont recommandés
- Profil des clientes: majoritairement dans la **quarantaine**.

### 3. Feature Engineering
- Ajout des colonnes `nbr_mots`, `nbr_char`: afin de prédire la recommandation en fonction  de la longueur des avis
- Ajout de la colonne `groupe_age`: afin de regrouper en tranches d'âges (< 30 ans, 30-40, 40-60, 60+)
- Ajout des colonnes afin de détecter si un mot-clé se retrouve dans l'avis: `fit`, `quality`, `color`, `love`, `size`

### 4. Analyse de sentiment (NLP)
- Tokenisation des mots avec `tidytext`
- Scoring via le **lexique Bing** (pour classer si les mots-clés représentent une connotation positive ou négative)
- Création des variables supplémentaires: `sent_positive`, `sent_negative`, `score_sentiment`

### 5. Modélisation
- **Régression Logistique**
- Variables sélectionnées pour la prédiction du modèle: `love`, `fit`, `quality`, `color`, `size`, `score_sentiment`
- Défi rencontré: il y a un déséquilibre des classes (81.8% "Oui"), le modèle prédit majoritairement "Recommandé".
  
---

## Résultats préliminaires

| Modèle | Accuracy | ROC-AUC |
|---|---|---|
| Régression Logistique | 81.7% | 0.652 |

---

## Technologies utilisées
- **Langage**: R
- **Packages**: `tidyverse`, `tidytext`, `tidymodels`, `ggplot2`, `janitor`, `skimr`
---

## Structure du projet

---
projet-mode-feminin/

  ├── data/                              
  ├── Projet_Tendance_Mode_féminin.Rmd  
  ├── Projet_Tendance_Mode_féminin.html 
  
  └── README.md                         
  
---
