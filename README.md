# SYS819
## Apprentissage automatique pour la Détection des anomalies dans les éoliennes

### Description
Ce projet a pour objectif de détecter des anomalies dans les éoliennes en utilisant des modèles d’autoencodeurs (AE). Quatre modèles ont été développés pour cette tâche :

1. **2 modèles entraînés sur des données avec journaux LOGS**  
2. **2 modèles entraînés sur des données sans journaux LOGS**

Pour chacun de ces cas :
- L'un des modèles a été entraîné sur des données normales.
- L'autre a été entraîné sur des données filtrées avec Isolation Forest.


## Directory Structure
The project is organized into two main directories:

### `with logs`
Contains scripts, data, and models trained using datasets with turbine logs.

#### Files:
1. **`AE-with logs.ipynb`**: 
   - Jupyter notebook implementing the autoencoder models using data with logs.
2. **`Data Collection and Preprocessing with logs.ipynb`**:
   - Notebook for preprocessing datasets with turbine logs.
3. **`Dataset Splitting with logs.ipynb`**:
   - Notebook for splitting datasets into training, validation, and testing subsets with logs.
   - Isolation forest
5. **Model Files**:
   - `autoencoder_IF_model.pth`: Trained Isolation Forest autoencoder.
   - `autoencoder_manual_model.pth`: Trained manual filtering autoencoder.
6. **Data Files**:
   - `final_data.csv`: Final processed dataset.
   - `train_data.csv`, `train_data_IF.csv`: Training datasets (manual and Isolation Forest-filtered).
   - `val_data.csv`: Validation dataset.
   - `test_data.csv`: Test dataset.
7. **Other Files**:
   - `Historical-Failure-Logbook.xlsx`, `Onsite-MetMast-SCADA-data.xlsx`: Source data for logs and SCADA signals.
   - `scaler.pkl`: Scaler used for data normalization.
   - `reconstruction_thresholds.pkl`: Threshold values for reconstruction error classification.

---

### `without logs`
Contains scripts, data, and models trained using datasets without turbine logs.

#### Files:
1. **`AE-without logs.ipynb`**: 
   - Jupyter notebook implementing the autoencoder models using data without logs.
2. **`Data Collection and Preprocessing without logs.ipynb`**:
   - Notebook for preprocessing datasets without turbine logs.
3. **`Dataset Splitting without logs.ipynb`**:
   - Notebook for splitting datasets into training, validation, and testing subsets without logs.
   - Isolation forest
4. **Model Files**:
   - `autoencoder_IF_model.pth`: Trained Isolation Forest autoencoder.
   - `autoencoder_manual_model.pth`: Trained manual filtering autoencoder.
5. **Data Files**:
   - `final_data.csv`: Final processed dataset.
   - `train_data.csv`, `train_data_IF.csv`: Training datasets (manual and Isolation Forest-filtered).
   - `val_data.csv`: Validation dataset.
   - `test_data.csv`: Test dataset.
6. **Other Files**:
   - `Historical-Failure-Logbook.xlsx`, `Onsite-MetMast-SCADA-data.xlsx`: Source data for SCADA signals.
   - `scaler.pkl`: Scaler used for data normalization.
   - `reconstruction_thresholds.pkl`: Threshold values for reconstruction error classification.

---

### Prérequis
#### Bibliothèques Python nécessaires
- `pandas`
- `numpy`
- `scikit-learn`
- `torch`
- `seaborn`
- `matplotlib`
- `joblib`

Pour installer les dépendances :
```bash
pip install pandas numpy scikit-learn torch seaborn matplotlib joblib
```

### Exécution des modèles

#### Évaluation des modèles
L’évaluation des modèles comprend :
- Calcul des erreurs de reconstruction.
- Comparaison des précisions, rappels et F1-scores.
- Analyse des faux positifs et faux négatifs.
- Visualisation des distributions des erreurs de reconstruction.

### Principaux Enseignements
Les résultats montrent que :
- **Les journaux logs ajoutent une valeur contextuelle**, améliorant les performances des modèles, bien qu’ils augmentent légèrement les faux positifs.
- **Isolation Forest** est efficace pour prétraiter les données, mais peut exclure certains cas limites pertinents pour l’apprentissage.
- Une base de données **plus propre et mieux équilibrée** aurait probablement produit des résultats plus convaincants.

### Limites et Suggestions d’Améliorations
- Les données SCADA étaient loin d’être parfaites, contenant de nombreux points erronés et seulement 30 anomalies documentées.
- Les journaux logs peuvent être traités en séparant les valeurs numériques (par exemple, température, tension) des chaînes de caractères, réduisant ainsi la dimensionnalité des embeddings.
- L’amélioration de la qualité des données reste une priorité pour maximiser les performances des modèles.

### Accès au Projet
Tout le code, les données, les résultats et les visualisations sont disponibles dans le dépôt GitHub :
[https://github.com/charbel-nsr/SYS819](https://github.com/charbel-nsr/SYS819)
