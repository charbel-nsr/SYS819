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


---

## Required Datasets
### Excel Files
The datasets used in this project were sourced from the EDP Open Data platform. Due to their size, these files are not included in this repository. **You must download the following files from EDP and place them in the appropriate directories (`with logs` and `without logs`):**

#### 2017:
1. **[Historical Failure Logbook 2017](https://www.edp.com/en/innovation/open-data/historical-failure-logbook-2017)** → Rename to `Historical-Failure-Logbook.xlsx`
2. **[Wind Farm Logs 2017](https://www.edp.com/en/innovation/open-data/wind-farm-logs-2017)** → Rename to `Wind-Turbines-Logs.xlsx`
3. **[Onsite Met Mast SCADA 2017](https://www.edp.com/en/innovation/open-data/onsite-metmast-scada-2017)** → Rename to `Onsite-MetMast-SCADA-data.xlsx`
4. **[Wind Turbine SCADA Signals 2017](https://www.edp.com/en/innovation/open-data/wind-turbine-scada-signals-2017)** → Rename to `Wind-Turbine-SCADA-signals.xlsx`

#### 2016:
5. **[Historical Failure Logbook 2016](https://www.edp.com/en/innovation/open-data/historical-failure-logbook-2016)** → Rename to `Historical-Failure-Logbook.xlsx`
6. **[Wind Turbine Logs 2016](https://www.edp.com/en/innovation/open-data/wind-turbine-logs-2016)** → Rename to `Wind-Turbines-Logs.xlsx`
7. **[Onsite Met Mast SCADA 2016](https://www.edp.com/en/innovation/open-data/onsite-metmast-scada-2016)** → Rename to `Onsite-MetMast-SCADA-data.xlsx`
8. **[Wind Turbine SCADA Signals 2016](https://www.edp.com/en/innovation/open-data/wind-turbine-scada-signals-2016)** → Rename to `Wind-Turbine-SCADA-signals.xlsx`

**Note**: they must be combined, renamed, duplicated and then placed in both the `with logs` and `without logs` directories.
---
### Produced CSV Files
The processed CSV files (`final_data.csv`, `train_data.csv`, `val_data.csv`, `test_data.csv`, etc.) generated during the preprocessing steps are also **not included** in this repository due to their large size. You will need to generate these CSV files yourself by first running the preprocessing scripts available in the respective directories (`Data Collection and Preprocessing with logs.ipynb` and `Data Collection and Preprocessing without logs.ipynb` then `Dataset Splitting with logs.ipynb` and `Dataset Splitting without logs.ipynb.ipynb`).

---

### Important Note
To execute the project successfully, ensure that:
1. All required Excel files are downloaded, renamed, and placed in the correct directories.
2. Run the preprocessing scripts to generate the necessary CSV files before training or evaluating the models.

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
