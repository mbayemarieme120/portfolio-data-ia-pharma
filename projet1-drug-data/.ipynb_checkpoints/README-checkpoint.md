# Projet 1 — Drug Reviews
## Description

Analyse complète d'un dataset de 161 297 avis patients sur des médicaments (2008-2017), combinant Python, SQL et Power BI pour extraire des insights actionnables dans un contexte pharmaceutique.

## Objectifs

- Identifier les médicaments les mieux perçus par les patients par condition médicale
- Analyser l'évolution temporelle de l'engagement patient
- Mesurer l'impact et l'utilité des avis par pathologie
- Visualiser la diversité thérapeutique par pathologie

## Stack technique

| Outil | Usage |
| --- | --- |
| Python (Pandas, NumPy) | Exploration et nettoyage des données |
| Matplotlib / Seaborn | Visualisations statistiques |
| SQL (SQLite) | Requêtes analytiques |
| Power BI | Dashboard interactif |

## Structure du projet

```
projet1-drug-reviews/
├── data/
│   ├── drugsComTrain_raw.tsv    ← dataset brut
│   └── drugsComTrain_clean.csv  ← dataset nettoyé
├── notebooks/
│   ├── 01_exploration.ipynb     ← EDA
│   ├── 02_nettoyage.ipynb       ← nettoyage
│   └── 03_sql_analyse.ipynb     ← requêtes SQL
├── dashboard/                   ← exports visuels
└── README.md
```

## Dataset

- **Source** : UCI Drug Reviews Dataset — Kaggle
- **Volume** : 161 297 avis patients
- **Période** : 2008 — 2017
- **Variables clés** : drugName, condition, rating, usefulCount, date

## Analyses réalisées

### 1. Exploration & Nettoyage

- Détection et suppression des résidus HTML dans la colonne `condition`
- Gestion des 899 valeurs manquantes remplacées par `Unknown`
- Conversion de la colonne `date` en datetime
- Suppression de la colonne `uniqueID` inutile
- Vérification : aucun doublon détecté

### 2. Analyse SQL — 3 angles d'analyse

**Dimension Qualité** — Médicaments les mieux notés par condition

Requête avec `GROUP BY drugName, condition` et `HAVING COUNT(*) >= 30` pour garantir la fiabilité statistique. Ces résultats constituent un signal de satisfaction patient utile pour orienter les stratégies de communication et de développement produit. Ces insights seraient croisés avec des données cliniques en entreprise pharma — c'est ce qu'on appelle le **benchmarking thérapeutique**.

**Dimension Temporelle** — Évolution des avis 2008-2017

Corrélation inverse entre volume d'avis et notes moyennes : biais de sélection en 2008 (notes ~9/10, peu d'avis), biais de la plainte en 2016 (notes ~6.3/10, pic d'activité). Cette tendance souligne l'importance de ne jamais interpréter les notes moyennes sans tenir compte du volume et du contexte temporel.

**Dimension Impact** — Top médicaments par avis utiles

Les pathologies générant le plus d'avis utiles sont la dépression, l'anxiété et la perte de poids, avec des notes moyennes autour de 7/10. L'engagement élevé malgré une note modérée suggère un fort besoin de communication patient et de support médical — information directement actionnable pour les équipes médicales et marketing.

### 3. Dashboard Power BI interactif

[Voir le dashboard interactif](https://app.powerbi.com/links/Lj42XHl9cg?ctid=654b4463-2e7e-4dee-b5b1-c828bfd6195e&pbi_source=linkShare)

![Aperçu du dashboard](..\dashboard\screenshot.png)

#### Conclusions du dashboard

**KPI Cards**

Le dataset couvre 161 297 avis patients sur 3 436 médicaments différents, avec une note moyenne globale de 6.99/10 — ce benchmark sert de référence pour toutes les analyses suivantes.

**Top médicaments les mieux notés**

Les médicaments les mieux évalués sont des traitements ciblés sur des pathologies précises. La note seule ne suffit pas à conclure à une supériorité clinique — ces résultats reflètent la satisfaction patient perçue et seraient croisés avec des essais cliniques en contexte R&D.

**Diversité thérapeutique par pathologie**

L'analyse du nombre de médicaments distincts par condition révèle des insights stratégiques importants pour l'industrie pharmaceutique. Une condition avec beaucoup de médicaments différents — comme Birth Control ou Pain — indique un **marché concurrentiel** où les entreprises investissent massivement en R&D. À l'inverse, une condition avec peu de médicaments indique un **besoin médical non couvert** — une opportunité de développement pour les entreprises du secteur.

**Évolution temporelle 2008-2017**

Le volume d'avis a explosé en 2016 avec une baisse simultanée des notes moyennes — traduisant la démocratisation de la parole patient et un biais de la plainte croissant. Les notes de 2008 (~9/10) reflètent un biais de sélection lié au faible nombre d'utilisateurs des plateformes d'avis à cette époque.

**Interactivité du dashboard**

Les slicers `condition` et `année` permettent de filtrer simultanément tous les visuels. En sélectionnant une pathologie, les KPI Cards, le barplot et la courbe temporelle se mettent à jour en temps réel — offrant une exploration dynamique des données par pathologie et par période.

## Insights clés

- La note moyenne globale est de **6.99/10**
- **Birth Control** est la condition avec la plus grande diversité thérapeutique
- Les notes ont baissé de 9/10 (2008) à 6.3/10 (2016) avec l'augmentation du volume d'avis
- La corrélation entre utilité et note est faible (r = 0.234) — la qualité de rédaction prime sur la note
- Les pathologies avec peu de médicaments représentent des opportunités de développement pharma

## Limites

Les conclusions sont basées sur des avis patients et ne se substituent pas aux essais cliniques. Ces insights constituent des signaux de satisfaction utiles pour orienter les stratégies de communication et de R&D, mais doivent être croisés avec des données cliniques pour toute décision thérapeutique.

## Auteure

**Marieme Mbaye**

Master 2 Compétences Complémentaires en Informatique — Université Claude Bernard Lyon 1

[LinkedIn](https://linkedin.com/in/marieme-mbaye)