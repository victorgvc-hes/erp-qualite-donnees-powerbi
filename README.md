<div align="center">

# Qualité des données ERP & contrôle opérationnel

### *Transformer les données brutes ERP en leviers décisionnels — avec Power BI*

<br/>

[![Power BI](https://img.shields.io/badge/Power%20BI-Desktop%20%26%20Service-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)](https://powerbi.microsoft.com)
[![Power Query](https://img.shields.io/badge/Power%20Query-ETL%20%26%20Validation-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)]()
[![DAX](https://img.shields.io/badge/DAX-Mesures%20Avanc%C3%A9es-0078D4?style=for-the-badge&logo=microsoft&logoColor=white)]()
[![Excel](https://img.shields.io/badge/Source-Excel%20%2F%20ERP-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)]()

<br/>

> **Problème réel. Données synthétiques. Impact opérationnel concret.**  
> Ce projet démontre comment un professionnel des achats avec 20+ ans d'expérience  
> traduit les lacunes ERP en tableaux de bord décisionnels prêts pour la production.

</div>

---

## Contexte & problématique

Les organisations dépendant de systèmes ERP font face à des défis persistants :

| Problème | Impact opérationnel |
|---|---|
| Visibilité limitée sur la qualité des données | Décisions basées sur des données erronées |
| Validation manuelle via Excel | Ressources mobilisées, erreurs humaines |
| Dépendance à des ressources clés | Risque de continuité opérationnelle |
| Détection tardive des anomalies | Coûts cachés et retards en cascade |

**Ce tableau de bord automatise la surveillance, détecte les anomalies et oriente les équipes vers les actions à haute valeur.**

---

## Aperçu du tableau de bord

### Onglet 1 — Vue d'ensemble : Qualité des données ERP

> Surveillance globale des commandes, anomalies et performance fournisseurs par période

![Vue d'ensemble – Qualité des données ERP](captures/tab1-overview.png)

**Ce qu'on voit en 10 secondes :**
- **500 commandes** analysées → **502 anomalies détectées** (certaines commandes en cumulent plusieurs)
- **366 commandes affectées** (73.2% du portefeuille)
- **291 livraisons en retard** — risque opérationnel critique
- Concentration chez 3 fournisseurs : **Ferantis, Gagnon Inc, Nordex** (>100 anomalies chacun)

---

### Onglet 2 — Diagnostic opérationnel : Analyse des anomalies

> Analyse cause-racine par acheteur, fournisseur, usine et niveau de risque

![Analyse des anomalies – Diagnostic opérationnel](captures/tab2-diagnostic.png)

**Insights clés révélés :**
- **Exposition financière estimée : 12,43 M$** — quantification directe du risque
- **J. Bouchard (83 anomalies)** — acheteur avec le taux le plus élevé, nécessite un audit
- **Niveau de risque Moyen domine (227)** vs Élevé (18) — opportunité d'intervention préventive
- Drill-down par fournisseur → catégorie → usine → acheteur possible en un clic

---

### Onglet 3 — Analyse des causes des anomalies

> Décomposition waterfall par type d'anomalie et arbre de causes racines par niveau de risque

![Analyse des causes des anomalies](captures/tab3-causes.png)

**Ce qu'on voit en 10 secondes :**
- **549 anomalies totales** décomposées en 6 catégories distinctes via un graphique en cascade
- **Livraison en retard (291)** et **Fournisseur non approuvé (140)** représentent 78% des anomalies — priorités d'action claires
- **Prix anormal (50), Date manquante (30), Quantité invalide (20), ID invalide (18)** — anomalies de données structurelles à corriger à la source ERP
- **Arbre de causes racines** : décomposition interactive des 348 anomalies par niveau de risque (Moyen : 227 / Faible : 103 / Élevé : 18)
- Possibilité de drill-down sur chaque nœud pour isoler les combinaisons fournisseur × type × risque

---
## Architecture & flux de données

<p align="center">
  <img src="captures/flux-de-donnees.png" alt="Flux de données — ERP vers Power BI" width="100%"/>
</p>

<p align="center">
  <em>De la source ERP à la décision opérationnelle — pipeline complet de transformation des données</em>
</p>

---

## Capacités techniques démontrées

### Power Query — ETL & validation
- Règles de validation métier appliquées à la source
- Détection automatisée de 5+ types d'anomalies (retards, écarts de prix, données manquantes…)
- Classification par niveau de risque (Faible / Moyen / Élevé)
- Transformation robuste et reproductible

### Modélisation des données
- **Schéma en étoile** optimisé pour la performance DAX
- Relations one-to-many correctement configurées
- Table de dates dédiée pour l'intelligence temporelle

### DAX — Mesures analytiques
```dax
-- Exemple : Taux d'anomalies
Taux Anomalies = 
DIVIDE(
    CALCULATE(COUNTROWS(Commandes), Commandes[Has_Anomalie] = TRUE()),
    COUNTROWS(Commandes),
    0
)

-- Exemple : Exposition financière estimée
Exposition Financière = 
CALCULATE(
    SUMX(Commandes, Commandes[Valeur_Commande]),
    Commandes[Has_Anomalie] = TRUE()
)
```

### Conception du tableau de bord
- Filtres croisés dynamiques (Usine / Acheteur / Fournisseur / Période)
- Drill-down hiérarchique : Fournisseur → Catégorie → Usine → Acheteur
- KPI cards avec seuils visuels
- Palette cohérente orientée lisibilité opérationnelle

---

## Résultats & impact simulé

| Indicateur | Valeur |
|---|---|
| Commandes analysées | 500 |
| Anomalies détectées | 502 |
| Taux d'anomalies | **73.2%** |
| Exposition financière estimée | **12,43 M$** |
| Livraisons en retard | 291 |
| Fournisseurs à risque concentré | 3 (Ferantis, Gagnon Inc, Nordex) |
| Acheteur avec le plus d'anomalies | J. Bouchard (83) |

---

## Pourquoi ce projet se distingue

Ce n'est pas un tutoriel reproduit. C'est la **traduction directe d'une expérience terrain** en solution analytique :

- **Domaine métier profond** : Les règles de validation reflètent de vraies pratiques d'achat (PO, réception, facturation)
- **Pensée système** : Du problème ERP → ETL → modèle → KPI → décision opérationnelle
- **Orientation ROI** : Chaque visuel répond à une question de gestion concrète
- **Scalable** : L'architecture supporte une connexion à un ERP réel (SAP, Oracle, Dynamics)

---

## Structure du dépôt

```
📁 erp-data-quality-powerbi/
├── 📊 PowerBI_Controle_Qualite_Donnees_ERP.pbix   # Fichier Power BI complet
├── 📁 donees/
│   └── donnees_erp_qualite_controles_powerbi.xlsx       # Données synthétiques source
├── 📁 captures/
│   ├── tab1-overview.png           # Vue d'ensemble
│   └── tab2-diagnostic.png         # Diagnostic opérationnel
│   └── tab3-causes.png             # Diagnostic opérationnel
│   └── 📄 flux-de-donnees.png      # Diagramme d'architecture
└── 📄 README.md
```

---

## Utilisation

```bash
# 1. Cloner le dépôt
git clone https://github.com/victorgvc-hes/erp-data-quality-powerbi.git

# 2. Ouvrir le fichier dans Power BI Desktop
#    File > Open > ERP_Data_Quality.pbix

# 3. Si nécessaire, actualiser la source de données
#    Home > Transform Data > Data Source Settings
```

**Prérequis** : [Power BI Desktop](https://powerbi.microsoft.com/fr-fr/desktop/) (gratuit)

---

## 👤 Auteur

<div align="center">

**Victor Vergara**

*Professionnel des achats et des opérations | 20+ ans en chaîne d'approvisionnement*  
*Spécialisation : IA/ML appliquée • Analytique avancée • Transformation numérique*

[![LinkedIn](https://img.shields.io/badge/LinkedIn-victor--vergara075-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/victor-vergara075/)
[![GitHub](https://img.shields.io/badge/GitHub-Portfolio%20complet-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/victorgvc-hes?tab=repositories)
[![Email](https://img.shields.io/badge/Email-victorgvc%40gmail.com-EA4335?style=for-the-badge&logo=gmail&logoColor=white)](mailto:victorgvc@gmail.com)

</div>

---

<div align="center">

*Ce projet fait partie d'un portefeuille de projets appliqués combinant expertise en chaîne d'approvisionnement et analytique avancée.*

</div>
