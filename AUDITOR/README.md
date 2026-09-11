# GitHub Portfolio Auditor

Système d'audit du portefeuille GitHub `digitaleflex` destiné à identifier les repositories actifs, maintenus, stratégiques, obsolètes, duplicatifs ou à archiver/supprimer.

## Objectif

Analyser **tous les repositories accessibles** et produire une cartographie exploitable avant toute opération de nettoyage.

Le système doit analyser :

- métadonnées du repository ;
- date de création ;
- date de dernière mise à jour ;
- activité des 24 derniers mois ;
- fréquence et volume des commits ;
- contenu réel du dépôt ;
- technologies et frameworks ;
- README et qualité documentaire ;
- statut public/privé/archivé ;
- indices de fork, clone, template, exemple ou prototype ;
- familles de projets et doublons ;
- pertinence stratégique pour E-Flex / HashCode / portfolio personnel ;
- niveau de maintenance observable ;
- taille et signaux de dette technique ;
- recommandation finale.

## Fenêtres temporelles

Les rapports utilisent plusieurs fenêtres :

- **0–90 jours** : activité récente ;
- **3–12 mois** : maintenance active ;
- **12–24 mois** : maintenance récente ;
- **24–36 mois** : ancienneté significative ;
- **>36 mois** : très probablement legacy, sauf justification stratégique.

La date seule ne déclenche jamais une suppression.

## Classification

Chaque repository reçoit une recommandation parmi :

### KEEP
Projet pertinent et suffisamment utile pour être conservé.

### KEEP_INTERNAL
Projet stratégique ou infrastructure interne à conserver mais pas nécessairement à exposer publiquement.

### CONSOLIDATE
Projet utile mais faisant partie d'une famille de doublons/versions et devant être fusionné avec un repository canonique.

### ARCHIVE
Historique utile mais développement terminé ou activité insuffisante.

### REMOVE_FROM_PUBLIC
Repository à conserver éventuellement pour historique mais à retirer du portfolio public.

### DELETE_CANDIDATE
Repository vide, doublon sans valeur, prototype abandonné ou contenu sans valeur durable, soumis à vérification humaine avant suppression.

## Score global

Le scoring recommandé :

```text
PortfolioScore =
  25% StrategicValue
+ 20% RecentActivity
+ 15% Maintenance
+ 15% ContentQuality
+ 10% Originality
+ 10% Documentation
+  5% PortfolioFit
```

Des pénalités séparées doivent être appliquées pour :

- duplication ;
- fork/clone évident ;
- dépôt vide ;
- prototype abandonné ;
- exposition publique inappropriée ;
- secrets ou données sensibles détectées.

## Règle de sécurité

Le système est **read-only par défaut**.

Il ne supprime, archive, renomme ou modifie aucun repository automatiquement.

Toute action destructive exige une décision humaine et, avant suppression :

1. vérifier les déploiements ;
2. vérifier les domaines et intégrations ;
3. vérifier les forks ;
4. vérifier les workflows ;
5. vérifier les dépendances externes ;
6. vérifier les releases/tags utiles ;
7. sauvegarder si nécessaire.

## Sorties

```text
AUDITOR/
├── README.md
├── SPEC.md
├── SCORING.md
├── RULES.md
├── schemas/
├── collectors/
├── analyzers/
├── scoring/
├── reports/
│   ├── inventory.csv
│   ├── activity-24m.csv
│   ├── content-analysis.csv
│   ├── duplicate-groups.csv
│   ├── recommendations.csv
│   ├── keep-list.md
│   ├── archive-list.md
│   ├── delete-candidates.md
│   └── portfolio-summary.md
└── scripts/
```

## Résultat attendu

Transformer un compte de plus de 200 repositories en un portefeuille clair :

```text
200+ repositories
       |
       v
Complete inventory
       |
       v
Activity + content analysis
       |
       v
Duplicate / legacy detection
       |
       v
Scoring
       |
       +--> KEEP
       +--> KEEP_INTERNAL
       +--> CONSOLIDATE
       +--> ARCHIVE
       +--> REMOVE_FROM_PUBLIC
       +--> DELETE_CANDIDATE
       |
       v
Curated GitHub Portfolio
```
