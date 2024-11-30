 Gestion des données industrielles

===========
.. figure:: /Documentation/Images/IM3.png
   :width: 100%
   :align: center
   :alt: Alternative text for the image
   :name: Pipeline


1.Gestion des données industrielles
-----------------------------------
# Gestion des données dans le tableau de bord industriel

Cette page explique comment les données industrielles sont collectées, traitées et affichées dans le tableau de bord. Elle couvre les étapes clés de l’intégration des sources de données, le traitement des données, et leur visualisation dans une interface utilisateur interactive.

## Étape 1 : Collecte des données

Le tableau de bord extrait les données de différentes sources industrielles, telles que :

- Capteurs connectés (IoT)
- Bases de données existantes (SQL, NoSQL)
- API externes fournies par des systèmes industriels tiers

### Exemple de script pour la collecte de données via une API :

```python
import requests

def collect_data_from_api(endpoint, headers):
    response = requests.get(endpoint, headers=headers)
    if response.status_code == 200:
        return response.json()  # Les données collectées sous format JSON
    else:
        raise Exception(f"Erreur {response.status_code} lors de la récupération des données.")
2.Traitement et nettoyage des données
---------------------------------------
Une fois les données collectées, elles doivent être nettoyées et transformées avant d’être visualisées.
import pandas as pd

def clean_and_normalize_data(data):
    df = pd.DataFrame(data)
    df.fillna(0, inplace=True)  # Remplir les valeurs manquantes
    df['timestamp'] = pd.to_datetime(df['timestamp'])  # Conversion en format datetime
    return df
3.Visualisation des données
----------------------------
Les données nettoyées sont affichées dans des graphiques interactifs pour faciliter l’analyse et la prise de décision.
import plotly.express as px

def visualize_production_data(df):
    fig = px.line(df, x='timestamp', y='production_rate', title='Taux de production au fil du temps')
    fig.show()
