# AI Security

## Objectif
Étudier la sécurité des systèmes IA modernes, particulièrement les applications utilisant des LLM et des agents.

## Threat model simplifié

Utilisateur / Donnée non fiable
        ↓
     Agent IA
        ↓
  Mémoire / Contexte
        ↓
     Tools / MCP
        ↓
 APIs / Infrastructure

Chaque couche doit être considérée comme une surface d'attaque.

## Questions de recherche
1. Comment limiter les actions d'un agent ?
2. Comment isoler les outils ?
3. Comment empêcher l'empoisonnement de mémoire ?
4. Comment contrôler les permissions ?
5. Comment auditer les décisions et actions ?

## Références à intégrer progressivement
- OWASP
- NIST AI Risk Management Framework
- MITRE ATT&CK
- recherches sur LLM et agent security