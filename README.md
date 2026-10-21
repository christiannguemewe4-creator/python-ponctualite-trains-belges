# Ponctualité des trains belges – Analyse Python (Infrabel, septembre 2026)

**Quand et où les trains belges prennent-ils du retard ?**
Analyse de 2,1 millions d'arrêts de trains à partir des données ouvertes d'Infrabel, avec Python et pandas.

---

## Le contexte

Infrabel, gestionnaire du réseau ferroviaire belge, publie chaque mois les données brutes de ponctualité : pour chaque train et chaque arrêt, l'heure prévue et l'heure réelle d'arrivée et de départ.

L'objectif de ce projet est d'identifier **les moments** (heures, jours) et **les endroits** (gares, lignes) où les retards se concentrent, puis d'en tirer des recommandations concrètes.

**Indicateur utilisé :** un train est considéré comme ponctuel s'il a **moins de 6 minutes de retard** (définition officielle d'Infrabel).

## Les données

| Élément | Détail |
|---|---|
| Source | [Infrabel Open Data](https://opendata.infrabel.be) – données brutes de ponctualité |
| Période | septembre 2026 |
| Volume | 2 067 492 lignes, 22 colonnes |
| Taille | ~349 Mo (non incluses dans le dépôt, voir « Reproduire l'analyse ») |

## Outils

Python 3.13 · pandas · matplotlib · Jupyter Notebook (VS Code)

## La démarche

1. **Chargement et nettoyage** : traitement des valeurs manquantes et nulles, conversion des dates et heures.
2. **Ponctualité globale** : part des trains à l'heure au départ et à l'arrivée.
3. **Quand ?** Taux de retard par heure de la journée et par jour de la semaine.
4. **Où ?** Taux de retard par gare et par ligne (gares de moins de 1 000 arrêts exclues).
5. **Le retard s'aggrave-t-il le long du trajet ?** Retard moyen selon le numéro d'arrêt.
6. **Recommandations.**

## Résultats clés

| Constat | Chiffre clé |
|---|---|
| Ponctualité globale | 92,6 % des départs et 92,5 % des arrivées à l'heure |
| Le retard est déjà là en début de trajet | 1,6 min de retard moyen dès le 1er arrêt, contre environ 0,75 min ajoutée ensuite |
| Les heures de pointe sont les plus touchées | ~9,5 % de retards à 8-9 h et 17-18 h, contre ~6 % en milieu de journée |
| L'heure compte plus que le jour | Mardi 8,3 % et vendredi 8,2 % (pires jours), mais l'écart entre les jours reste faible |
| 5 lignes concentrent les retards | Lignes 25, 36N, 36, 96 et 37 : 29 % des arrivées en retard |
| Le retard s'aggrave peu en route | De 1,6 à ~2,4 minutes de retard moyen le long du trajet |

## Recommandations

1. **Faire partir les trains à l'heure** : dès le premier arrêt, les trains ont déjà 1,6 minute de retard en moyenne, et ce retard se retrouve à l'arrivée.
2. **Renforcer la régulation du trafic aux heures de pointe** (8-9 h et 17-18 h).
3. **Concentrer les efforts sur 5 lignes**, en priorité la **ligne 37 (Liège–Verviers–Welkenraedt)**, qui cumule un taux de retard élevé (16,2 %) et un fort volume.

## Limites

- Un seul mois de données : les résultats peuvent varier selon la saison (météo, vacances, travaux).
- Les gares de moins de 1 000 arrêts ont été exclues pour éviter des pourcentages trompeurs.
- L'explication du mercredi plus calme (temps partiels, horaires scolaires) reste une hypothèse à vérifier.

**Pistes pour aller plus loin :** analyser plusieurs mois pour confirmer les tendances, et croiser avec des données météo ou de travaux.

## Structure du dépôt

```
├── analyse_ponctualite.ipynb   # notebook complet (code, graphiques, conclusions)
├── README.md
└── .gitignore                  # exclut le dossier data/
```

## Reproduire l'analyse

1. Télécharger les données brutes de ponctualité de septembre 2026 sur [Infrabel Open Data](https://opendata.infrabel.be).
2. Placer le fichier dans un dossier `data/` à la racine du projet, sous le nom `data/Data_raw_punctuality_202609.csv`.
3. Ouvrir `analyse_ponctualite.ipynb` et exécuter toutes les cellules.

---

**Auteur :** Christian Nguemewe – Junior Data Analyst
[LinkedIn](https://www.linkedin.com/in/christian-nguemewe) · [GitHub](https://github.com/christiannguemewe4-creator)
