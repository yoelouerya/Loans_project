# 🚀 AI-Driven Loan Status Prediction System

## Description du projet
Ce projet vise à prédire le **statut d’un prêt bancaire (accepté ou refusé)** à partir de données clients à l’aide de **techniques de Machine Learning**.  
L’objectif est de construire un **système d’aide à la décision bancaire** capable d’évaluer le risque de chaque demande et de fournir un **score de confiance (Risk_score)** associé à chaque prédiction.

Étant donné que les données ne sont pas volumineuses, le modèle repose sur un **SVM (Support Vector Machine)** avec un **kernel RBF**, choisi pour sa robustesse face aux données non linéaires et déséquilibrées et pour éviter également le biais ou le surapprentissage.

Ce projet combine :
- 📊 **Analyse exploratoire** et détection d’anomalies (EDA)
- ⚙️ **Prétraitement avec Python(scikit-learn, pandas, numpy...)** (nettoyage, encodage, normalisation)
- 🤖 **Apprentissage automatique supervisé (SVM)**
- 📊 **Visualisation de l'hyperplan séparant les 2 classes**
- 💡 **Analyse IA et reporting interactif sous Power BI(DAX)**

---

## Structure du code

### 1. **Importation et analyse initiale**
- Lecture du dataset `loan_status.csv`
- Exploration des valeurs manquantes et de la distribution des variables
- Analyse croisée de `Credit_History` et `Loan_Status`
- Détection et visualisation des **outliers** sur `ApplicantIncome`, `CoapplicantIncome`, et `LoanAmount`

### 2. **Nettoyage et préparation des données**
- Remplissage intelligent des valeurs manquantes :
  - `Gender`, `Dependents`, `Married`, `Credit_History`, `Self_Employed`
- Remplacement des modalités spécifiques (`3+` → `4`)
- Traitement des valeurs extrêmes avec **log transformation**
- Normalisation des variables numériques via **StandardScaler**
- Encodage des variables catégorielles (`Gender`, `Married`, `Education`, etc.)

### 3. **Modélisation (SVM Classifier)**
- Division du dataset en **train/test (80/20)**
- Entraînement d’un **SVC(kernel='rbf', C=1, gamma='scale')**
- Visualisation de la **frontière de décision du modèle**
- Évaluation avec :
  - Accuracy
  - Recall, Precision, F1-score
  - Matrice de confusion
  - **AUC ROC Score**

### 4. **Prédictions et exportation**
- Calcul des prédictions finales (`Loan_Status_predict`)
- Calcul du **Risk_Score** = probabilité d’approbation (`predict_proba`)
- Exportation du fichier complet `LoanStatus.csv` pour Power BI

---

## 📊 Colonnes exportées vers Power BI

| Colonne | Description |
|----------|-------------|
| `Loan_ID` | Identifiant unique du prêt |
| `Gender` | Sexe de l’emprunteur |
| `Married` | Statut marital |
| `Dependents` | Nombre de personnes à charge |
| `Education` | Niveau d’études |
| `Self_Employed` | Statut d’emploi |
| `ApplicantIncome` | Revenu principal |
| `CoapplicantIncome` | Revenu du co-emprunteur |
| `LoanAmount` | Montant du prêt demandé |
| `Credit_History` | Historique de crédit |
| `Property_Area` | Zone géographique |
| `Loan_Status` | Décision réelle (‘Y’ / ‘N’) |
| `Loan_Status_predict` | Prédiction du modèle (1 = accepté, 0 = refusé) |
| `Risk_Score` | Probabilité d’acceptation prédite (entre 0 et 1) |

---

## 📈 Intégration Power BI — AI-Driven Analytics

Une fois le fichier `LoanStatus.csv` importé dans Power BI :
- Crée une **page “AI-Insights”** :
  - Comparaison `Loan_Status` (réel) vs `Loan_Status_predict` (IA)
  - Visualisation du **taux d’acceptation par genre, zone, éducation**
  - Graphiques combinant **Risque moyen (Risk_Score)** et **taux réel**
- Crée une **page “Model Performance”** :
  - Tableau `Model_Scores` avec les mesures DAX :
    - Accuracy, Precision, Recall, F1-score
    - TP, FP, TN, FN
  - Visualisation dynamique par segment (genre, zone, etc.)
- Crée une **page “Decision Support”** :
  - Système de scoring IA dynamique
  - Indicateurs visuels : “Approuver / Refuser” selon seuils de risque

---

## Scores de performance (exemple)

| Metric | Value |
|---------|--------|
| Accuracy | 0.80 |
| Precision (classe 1) | 0.89 |
| Recall (classe 1) | 0.93 |
| Recall (classe 0) | 0.45 |
| F1-score | 0.82 |
| AUC | 0.85 |


## Technologies utilisées
- **Python 3.11+**
- **Pandas / NumPy / Matplotlib**
- **Scikit-learn**
- **Power BI Desktop**
- **DAX** pour les mesures analytiques

---


## 🏆 Auteur
**Nom :** Youness EL OUERYAGHELY 
**Spécialité :** Data & Information Systems Engineering  
**Projet académique :** AI-Driven Loan Risk & Acceptance Prediction  
**Année :** 2025  

---

## 📁 Fichiers du projet
```
│
├── loan_status.csv          # Jeu de données original
├── loan_status.ipynb        # Notebook complet du projet
├── LoanStatus.csv           # Fichier nettoyé et enrichi pour Power BI
└── README.md                # Description complète du projet
```

---

## Exemple de ligne exportée :
| Loan_ID | Gender | Married | ApplicantIncome | LoanAmount | Loan_Status | Loan_Status_predict | Risk_Score |
|----------|--------|----------|-----------------|-------------|--------------|---------------------|-------------|
| LP001002 | Male | Yes | 5849 | 146 | Y | 1 | 0.92 |

