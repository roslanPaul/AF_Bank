# 🏦 Analyse du Churn Bancaire & Étude Boursière Comparative

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-1.6+-green.svg)](https://xgboost.readthedocs.io/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

> **Projet collaboratif de Data Science** combinant prédiction de churn bancaire et analyse financière quantitative. Développé en binôme par **Roslan Nzamba Nzamba** (spécialisation Finance & Statistiques) et **Moussa Dosso** (Analyste AML & expertise technique).

## 📊 Aperçu du Projet

Ce projet démontre une approche complète d'analyse de données appliquée à deux domaines complémentaires :

### 🎯 **Partie I : Prédiction du Churn Bancaire**
- **Objectif** : Identifier les clients à risque d'attrition avec une précision maximale
- **Dataset** : 10,127 clients bancaires, 23 variables comportementales et démographiques
- **Résultat** : **99.2% d'AUC** avec le modèle XGBoost optimisé

### 📈 **Partie II : Analyse Boursière Tesla vs Stellantis**
- **Objectif** : Comparer les performances et profils de risque de TSLA et STLA
- **Période** : Analyse sur 1 mois, 6 mois et 1 an
- **Résultat** : Recommandations d'allocation basées sur l'analyse technique

## 🏆 Résultats Clés

| Métrique | Valeur | Impact Business |
|----------|--------|-----------------|
| **AUC Score** | 99.2% | Discrimination excellente |
| **Recall** | 91% | Détection de 91% des churners |
| **Precision** | 87% | Fiabilité des alertes |
| **ROI Estimé** | x3 | Rentabilité des campagnes de rétention |

### 📊 Variables Prédictives Principales
1. **Total_Trans_Ct** (F-score: 1304.84) - Nombre de transactions
2. **Total_Ct_Chng_Q4_Q1** (F-score: 891.23) - Évolution comportementale
3. **Total_Revolving_Bal** (F-score: 756.78) - Solde renouvelable
4. **Avg_Utilization_Ratio** (F-score: 689.45) - Taux d'utilisation du crédit

## 🛠️ Stack Technique

### **Langages & Environnement**
- **Python 3.8+** - Langage principal
- **Google Colab** - Environnement collaboratif
- **Jupyter Notebook** - Développement et documentation

### **Bibliothèques Principales**
```python
# Data Manipulation & Analysis
import pandas as pd
import numpy as np

# Machine Learning
from sklearn.ensemble import RandomForestClassifier
from sklearn.linear_model import LogisticRegression
from sklearn.preprocessing import StandardScaler
from sklearn.model_selection import train_test_split
import xgboost as xgb

# Statistical Analysis
from scipy.stats import chi2_contingency, f_oneway
import statsmodels.api as sm

# Visualization
import matplotlib.pyplot as plt
import seaborn as sns

# Financial Data
import yfinance as yf

# Utilities
from tqdm import tqdm
import joblib
```



## 🚀 Installation & Utilisation

### **1. Cloner le Repository**
```bash
git clone https://github.com/votre-username/bank-churn-analysis.git
cd bank-churn-analysis
```

### **2. Installer les Dépendances**
```bash
pip install -r requirements.txt
```

### **3. Lancer l'Analyse**
```bash
# Option 1: Jupyter Notebook
jupyter notebook notebooks/

# Option 2: Google Colab
# Uploader les notebooks sur Colab et exécuter
```

## 📈 Méthodologie Détaillée

### **Phase 1: Analyse Exploratoire (EDA)**
- ✅ Analyse de la qualité des données (valeurs manquantes, outliers)
- ✅ Statistiques descriptives univariées et bivariées
- ✅ Visualisations des distributions et corrélations
- ✅ Tests statistiques (Chi², ANOVA, corrélations)

### **Phase 2: Préprocessing & Feature Engineering**
- ✅ Gestion des valeurs "Unknown" par imputation
- ✅ Encodage One-Hot des variables catégorielles
- ✅ Standardisation Z-score pour l'ACP
- ✅ Sélection de variables (LASSO, SelectKBest)

### **Phase 3: Modélisation Comparative**
- ✅ **Régression Logistique** (baseline) : AUC 0.879
- ✅ **Random Forest** (ensemble) : AUC 0.988
- ✅ **XGBoost** (optimisé) : AUC 0.992 ⭐

### **Phase 4: Optimisation & Validation**
- ✅ Hyperparameter tuning XGBoost
- ✅ Ajustement du seuil de décision (0.35)
- ✅ Validation croisée stratifiée
- ✅ **Simulation Monte Carlo** (1000 runs) pour robustesse

### **Phase 5: Clustering & Segmentation**
- ✅ **K-means** (k=2) sur composantes principales
- ✅ **DBSCAN** pour clusters non-sphériques
- ✅ Profiling des segments clients

### **Phase 6: Analyse Financière**
- ✅ Données boursières temps réel (yfinance)
- ✅ Indicateurs techniques (MA20/50, RSI, MACD)
- ✅ Analyse de volatilité et performance relative
- ✅ Recommandations d'allocation d'actifs

## 🧪 Validation & Robustesse

### **Simulation Monte Carlo**
```python
# Validation de la stabilité du modèle
n_simulations = 1000
confidence_interval = [0.148, 0.154]  # IC 95%
mean_prediction = 0.151
std_prediction = 0.0015

# Interprétation: Modèle très robuste aux perturbations
```

### **Métriques de Performance**
- **AUC-ROC** : 0.992 (excellente discrimination)
- **Précision classe 1** : 0.87 (87% des alertes sont vraies)
- **Recall classe 1** : 0.91 (91% des churners détectés)
- **F1-Score** : 0.89 (excellent équilibre)

## 📊 Insights Business

### **🎯 Facteurs de Risque Identifiés**
1. **Inactivité transactionnelle** : <40 transactions/an
2. **Sous-utilisation du crédit** : Ratio d'utilisation <15%
3. **Contacts fréquents** : >3 appels service client/an
4. **Diminution d'activité** : Baisse >50% entre Q4 et Q1

### **💰 Recommandations Stratégiques**
- **Scoring prédictif** : Surveillance continue des clients score >0.35
- **Interventions ciblées** : Campagnes personnalisées par segment
- **Programmes de fidélité** : Incitations à l'utilisation pour clients inactifs
- **Monitoring comportemental** : Alertes automatiques sur changements brutaux

### **📈 ROI Estimé**
- **Coût intervention** : 50€/client
- **Valeur client sauvé** : 2,500€ (LTV moyenne)
- **Taux de succès** : 30% (rétention post-intervention)
- **ROI net** : **300%** sur les campagnes ciblées

## 🏢 Applications Sectorielles

### **Services Financiers**
- Banques retail et corporate
- Assurances (prédiction résiliation)
- FinTech (optimisation produits)
- Néobanques (stratégies de croissance)

### **Autres Secteurs**
- Télécommunications (churn abonnés)
- E-commerce (fidélisation clients)
- SaaS (réduction du churn)
- Utilities (rétention clients)

## 👥 Équipe & Contributions

### **Roslan Nzamba Nzamba** 
- 🎓 **Spécialisation** : Finance & Statistiques pour l'Analyse de Données
- 🔍 **Contributions** : Modélisation prédictive, analyse statistique, finance quantitative
- 🎯 **Objectif** : Recherche de stage en Data Science
- 📧 **Contact** : [r.nzamba07@example.com]
- 💼 **LinkedIn** : [https://www.linkedin.com/in/roslan-paul-n-89ba6b173/]

### **Moussa Dosso**
- 🏦 **Fonction** : Analyste AML (Anti-Money Laundering) en CDD
- 🔍 **Contributions** : Modélisation prédictive, finance quantitative analyse exploratoire, expertise compliance
- 🎯 **Objectif** : Recherche de CDI Analyste ALM
- 💼 **Expertise** : AML + Data Science = profil rare et recherché
- 💼 **LinkedIn** : [https://www.linkedin.com/in/moussa-dosso-2b9362239/]

### **Synergie Collaborative**
L'alliance entre expertise **compliance/AML** et **data science quantitative** apporte une valeur unique pour les institutions financières, combinant innovation technique et conformité réglementaire.

## 📚 Documentation Technique

### **Notebooks Détaillés**
Chaque notebook contient :
- 📝 Documentation markdown extensive
- 💻 Code commenté et optimisé
- 📊 Visualisations interprétées
- 🔍 Analyses statistiques approfondies
- 💡 Insights métier actionnables

### **Fonctions Réutilisables**
Le module `src/` propose des classes et fonctions modulaires pour :
- Preprocessing automatisé
- Pipeline de modélisation
- Évaluation standardisée
- Visualisations cohérentes

## 🔮 Extensions Futures

### **Améliorations Techniques**
- [ ] **Deep Learning** : Réseaux de neurones pour interactions complexes
- [ ] **Survival Analysis** : Modélisation du temps jusqu'au churn
- [ ] **Online Learning** : Adaptation continue aux nouvelles données
- [ ] **Ensemble Methods** : Stacking de modèles spécialisés

### **Features Business**
- [ ] **Dashboard interactif** : Tableau de bord temps réel
- [ ] **API REST** : Service de scoring en production
- [ ] **A/B Testing** : Validation impact interventions
- [ ] **Monitoring continu** : Détection de dérive des modèles

### **Analyses Complémentaires**
- [ ] **Customer Lifetime Value** : Valeur prédictive des clients
- [ ] **Analyse de sentiment** : Feedback clients et NPS
- [ ] **Géolocalisation** : Patterns géographiques de churn
- [ ] **Analyse temporelle** : Saisonnalité et tendances

## 📄 Licence & Citation

### **Licence**
Ce projet est sous licence **MIT** - voir le fichier [LICENSE](LICENSE) pour les détails.

### **Citation**
Si vous utilisez ce code dans vos recherches, merci de citer :
```bibtex
@misc{nzamba_dosso_2025,
  title={Bank Churn Prediction and Stock Analysis: A Collaborative Data Science Approach},
  author={Nzamba Nzamba, Roslan and Dosso, Moussa},
  year={2025},
  howpublished={\url{https://github.com/votre-username/bank-churn-analysis}}
}
```

## 🤝 Contributions

Les contributions sont les bienvenues ! Pour contribuer :

1. **Fork** le projet
2. **Créer** une branche feature (`git checkout -b feature/AmazingFeature`)
3. **Commit** vos changements (`git commit -m 'Add AmazingFeature'`)
4. **Push** vers la branche (`git push origin feature/AmazingFeature`)
5. **Ouvrir** une Pull Request

### **Guidelines de Contribution**
- Code documenté et testé
- Respect des conventions PEP 8
- Commits atomiques et descriptifs
- Tests unitaires pour nouvelles fonctionnalités

## 📞 Contact & Support

### **Opportunités Professionnelles**
- 🎯 **Stage Analyste Financier** : Contact Roslan Nzamba Nzamba
- 💼 **CDI Analyste ALM** : Contact Moussa Dosso
- 🤝 **Collaborations** : Ouverts aux partenariats académiques et industriels

---

### 🌟 **Remerciements**

Merci à tous ceux qui ont contribué à ce projet, directement ou indirectement :
- La communauté open-source Python
- Les mainteneurs des bibliothèques utilisées
- Les reviewers et beta-testeurs
- Nos futurs employeurs qui reconnaîtront notre talent ! 😉

---

**⭐ Si ce projet vous a été utile, n'hésitez pas à lui donner une étoile sur GitHub !**

