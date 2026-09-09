# 💎 Emerging Gems — September 2026 Update

> **Purpose:** enrichir le radar avec des projets récents à fort potentiel et les transformer en pistes d'analyse concrètes.

## 🔥 New Research Candidates

### 1. OpenOSINT
**Repository:** https://github.com/OpenOSINT/OpenOSINT  
**Domaine:** OSINT · AI Agents · Security Research  
**Pourquoi le suivre:** agent OSINT open source avec REPL interactif, serveur MCP et CLI. La version annoncée en août 2026 est v2.27.0.  
**Statut:** Deep Research  
**Question à étudier:** quelles capacités sont réellement fiables pour automatiser une investigation OSINT sans dégrader la qualité des preuves ?

### 2. ADR — Agentic AI Detection and Response
**Repository:** https://github.com/uber/ADR  
**Domaine:** Agentic Security · AI Security · Detection & Response  
**Pourquoi le suivre:** système de sécurité pour agents IA avec observabilité, threat detection, benchmarking et mécanismes de prévention ; le projet indique un déploiement en production chez Uber.  
**Statut:** Deep Research  
**Question à étudier:** quelles briques d'observabilité et de contrôle pourraient être réutilisées dans notre architecture ?

### 3. AgentMem
**Repository:** https://github.com/JaceHo/AgentMem  
**Domaine:** Agent Memory · MCP · AI Coding  
**Pourquoi le suivre:** mémoire persistante locale pour agents de développement avec plusieurs niveaux de mémoire, hooks et mécanismes de retrieval.  
**Statut:** Research Candidate  
**Question à étudier:** quel compromis entre qualité de rappel, coût en tokens et complexité opérationnelle ?

### 4. codebase-memory-mcp
**Repository:** https://github.com/SuperCodeAgents/code-memory-mcp  
**Domaine:** Code Intelligence · Agent Memory · MCP  
**Pourquoi le suivre:** indexation structurelle de codebases et knowledge graph destinés aux agents de développement ; le projet annonce le support de 158 langages.  
**Statut:** Research Candidate  
**Question à étudier:** quelle valeur apporte son approche AST/LSP par rapport à une simple recherche sémantique ?

### 5. shared-agent-memory
**Repository:** https://github.com/dan-calin/shared-agent-memory  
**Domaine:** Shared Memory · MCP · Multi-Agent  
**Pourquoi le suivre:** partage d'une mémoire commune entre plusieurs agents via MCP, avec garde-fous orientés secrets et knowledge graph.  
**Statut:** Watch  
**Question à étudier:** comment gérer mémoire partagée, confidentialité et isolation dans une équipe multi-agents ?

## 📊 Priorisation initiale

| Projet | Innovation | Utilité potentielle | Facilité d'expérimentation | Priorité |
|---|---:|---:|---:|---|
| OpenOSINT | 5/5 | 5/5 | 4/5 | P0 |
| ADR | 5/5 | 5/5 | 3/5 | P0 |
| AgentMem | 4/5 | 5/5 | 5/5 | P1 |
| codebase-memory-mcp | 5/5 | 5/5 | 4/5 | P1 |
| shared-agent-memory | 4/5 | 4/5 | 5/5 | P1 |

> Ces scores sont des **scores de triage**, pas une évaluation finale. Ils doivent être confirmés par une analyse technique, des tests et une vérification de l'activité du projet.

## 🧪 Expérimentations proposées

### EXP-001 — Agent OSINT
**Objectif:** tester OpenOSINT sur un cas d'investigation bénin et documenté.  
**Mesures:** couverture des sources, qualité des citations, temps d'investigation, faux positifs.

### EXP-002 — Agent Security Monitoring
**Objectif:** étudier l'architecture d'ADR et reproduire un mini flux d'observabilité pour un agent local.  
**Mesures:** visibilité des appels outils, détection d'actions à risque, qualité des traces.

### EXP-003 — Persistent Coding Memory
**Objectif:** comparer AgentMem et codebase-memory-mcp sur un même repository.  
**Mesures:** pertinence du contexte récupéré, latence, consommation de tokens, facilité d'intégration.

## ✅ Prochaine règle de sélection

Un projet ne doit pas entrer dans **High Priority** uniquement parce qu'il est populaire.

Il doit montrer au minimum :

- activité récente et maintenue ;
- documentation exploitable ;
- architecture compréhensible ;
- possibilité d'expérimentation ;
- valeur concrète pour AI, Web, Cybersecurity ou Developer Infrastructure ;
- risques identifiés.
