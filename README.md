# 🔄 Package R pour Modèles de Mélanges Gaussiens

<div align="center">

![R](https://img.shields.io/badge/R-%3E%3D4.0.0-blue)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Status](https://img.shields.io/badge/Status-Research-orange)
![Update](https://img.shields.io/badge/Update-Feb%202024-green)


</div>

## 📋 Présentation
Implementation d'un package R fonctionnel pour les modèles de mélanges gaussiens, avec un focus sur la robustesse numérique et la flexibilité des structures de covariance. L'estimation des paramètres est réalisée via l'algorithme EM (Expectation-Maximization).

## ✨ Caractéristiques principales
Quatre hypothèses de covariance supportées pour une flexibilité maximale :
- Full 
- Tied
- Diagonal 
- Spherical 

Fonctionnalités avancées intégrées :
- Stabilité numérique optimisée 
- Sélection automatique du nombre de clusters par critères AIC/BIC
- Initialisation multiple avec sélection du meilleur modèle
- Décomposition SVD pour l'inversion des matrices
- Régularisation paramétrable des matrices de covariance
- Diagnostic complet de convergence
- Visualisations intégrées des résultats

## 💻 Installation et Configuration

### Prérequis
Le package nécessite R version 4.0.0 ou supérieure et les dépendances suivantes :
```r
install.packages(c("devtools", "mvtnorm", "ggplot2"))
```

### Installation depuis les sources
```r
# Installation depuis le dossier source local
install.packages("chemin/vers/le/dossier/du/package", repos = NULL, type = "source")
```

### 🚀 Utilisation rapide

Le package propose une interface intuitive pour l'estimation des mélanges gaussiens. Voici un exemple complet d'utilisation :

```r
# Étape 1 : Chargement du package
library(GaussianMixture)

# Étape 2 : Préparation des données
# Assurez-vous que vos données sont sous forme de matrice numérique
data <- as.matrix(your_data)

# Étape 3 : Configuration et initialisation du modèle
model <- MelangeGaussien$new(
    nb_clusters = 3,             # Nombre de composantes gaussiennes
    type_covariance = "full",    # Type de matrice de covariance
    nb_initialisations = 10,     # Nombre de départs aléatoires
    epsilon_convergence = 1e-4,   # Critère de convergence
    regul_inversibilite = 1e-6   # Paramètre de régularisation
)

# Étape 4 : Apprentissage du modèle
resultats <- model$fit(data)

# Étape 5 : Analyse des résultats
# Afficher les paramètres estimés
print(model$proportions)         # Proportions du mélange
print(model$moyennes)            # Centres des clusters
print(model$covariances)         # Matrices de covariance

# Étape 6 : Prédiction sur de nouvelles données
clusters <- model$predict(new_data)

# Étape 7 : Visualisation et diagnostic
model$plot_convergence()         # Visualiser la convergence
model$plot_clusters()            # Visualiser les clusters
```

## 📊 Résultats expérimentaux

Le package a été rigoureusement validé sur différents jeux de données :

### Données synthétiques 2D
- Validation sur 3 clusters gaussiens avec différents niveaux de chevauchement
- Test exhaustif des quatre structures de covariance
- Analyse comparative des critères AIC/BIC



## 📫 Contact

Pour toute question ou suggestion :
- Email : mehdi.mansour@univ-lyon2.fr

## 📜 Licence

Ce projet est sous licence MIT, permettant une utilisation libre dans des projets académiques et commerciaux. Voir le fichier `LICENSE` pour plus de détails.

---

<div align="center">

*Développé dans le cadre d'un projet académique*
*ICOM - Département Informatique*

</div>
