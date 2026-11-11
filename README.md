# Supervision des traitements batch – Stage CDG

Application web développée pendant mon stage à la **Caisse de Dépôt et de Gestion (CDG)** en juin 2025, en binôme : elle permet de **planifier, exécuter et superviser des jobs batch**, et de suivre leurs succès et leurs échecs dans un tableau de bord.

> 🔒 **Confidentialité.** Ce projet a été réalisé dans le cadre d'un stage en entreprise. Le code source n'est pas publié. Seules des captures d'écran avec des **données fictives** sont présentées ici.

## Problème traité

Les traitements batch (sauvegardes, rapports, archivages) tournent souvent la nuit, sans surveillance. Quand l'un d'eux échoue ou prend du retard, on ne le découvre que tard. L'objectif était de centraliser leur planification et leur suivi pour **repérer rapidement les erreurs et les retards**.

## Fonctionnalités

- **Gestion des jobs** : création, modification et suppression, avec la périodicité (quotidienne, hebdomadaire ou mensuelle), l'heure d'exécution et le responsable
- **Planificateur automatique** : exécution des jobs à l'heure prévue, selon leur périodicité
- **Historique des exécutions** : date, heure de début et de fin, statut (succès ou échec, avec le message d'erreur)
- **Lancement manuel** d'un job depuis l'interface
- **Tableau de bord** : nombre de jobs, jobs lancés et non lancés, filtre par responsable
- **Détection des jobs jamais lancés**
- **Tests de robustesse** : injection d'échecs simulés pour vérifier que les erreurs sont bien remontées et enregistrées

## Architecture

```
 Interface web (Django / Dash)
        │  création et suivi des jobs
        ▼
 Base de données (SQLite) : jobs et historique des exécutions
        ▲
        │  enregistre chaque exécution (succès ou échec)
 Planificateur Python (bibliothèque schedule)
        │  lance les jobs à l'heure prévue
        ▼
 Scripts batch
```

## Captures d'écran

### 1. Liste des jobs planifiés
![Liste des jobs](01-liste-jobs.png)

### 2. Ajout d'un job
![Ajout d'un job](02-ajout-job.png)

### 3. Historique des exécutions (succès et échecs)
![Historique des exécutions](03-historique-executions.png)

### 4. Tableau de bord
![Tableau de bord](04-tableau-de-bord.png)

## Technologies

Python · Django · Dash (Plotly) · Pandas · SQLite · bibliothèque `schedule` · Bash

## Ce que ce projet m'a apporté

- La supervision d'une chaîne de traitements : détecter un échec et en conserver la trace
- L'analyse de logs et d'indicateurs pour repérer les erreurs et les retards
- Le développement d'une application web complète en Python, en binôme

## Auteure

Hiba Jelloul, [github.com/hiba-jl](https://github.com/hiba-jl)
