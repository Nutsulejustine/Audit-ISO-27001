# Audit de conformité ISO/CEI 27001 — NovaPay SARL

Exercice pédagogique GRC : audit interne de conformité fictif, réalisé en continuité de la [PSSI](../01-PSSI/README.md) et de l'[analyse de risques EBIOS RM](../02-Analyse-risques-EBIOS-RM/README.md) de NovaPay SARL.

## Sommaire

1. [Contexte de l'audit](#1-contexte-de-laudit)
2. [Synthèse des constats par domaine](#2-synthèse-des-constats-par-domaine)
3. [Statement of Applicability (extrait)](#3-statement-of-applicability-extrait)
4. [Détail des écarts](#4-détail-des-écarts)
5. [Plan d'actions correctives](#5-plan-dactions-correctives)
6. [Conclusion et recommandation](#6-conclusion-et-recommandation)

---

## 1. Contexte de l'audit

**Objectif.** Vérifier le niveau de conformité du Système de Management de la Sécurité de l'Information (SMSI) de NovaPay SARL par rapport aux exigences de l'Annexe A de la norme ISO/CEI 27001:2022, en vue d'une future certification.

**Référentiel.** ISO/CEI 27001:2022 (Annexe A, 93 mesures réparties en 4 thèmes : organisationnelles, personnes, physiques, technologiques).

**Périmètre.** Les mêmes actifs que ceux couverts par la PSSI et l'analyse de risques EBIOS RM — application mobile, back-office, API de paiement, données clients.

**Méthode.** Entretiens avec le RSSI et le DSI (fictifs), revue documentaire de la PSSI et des procédures existantes, échantillonnage de contrôles techniques (gestion des accès, journalisation, sauvegardes).

**Échelle de maturité utilisée :**

| Niveau | Libellé | Description |
| --- | --- | --- |
| 0 | Inexistant | Aucune mesure en place |
| 1 | Initial | Mesure appliquée de façon ad hoc, non documentée |
| 2 | Partiel | Mesure documentée mais appliquée de façon incomplète |
| 3 | Défini | Mesure appliquée de façon systématique et documentée |
| 4 | Maîtrisé | Mesure mesurée, revue et améliorée en continu |

**Type d'audit.** Audit interne de conformité, réalisé en amont d'un audit de certification externe.

## 2. Synthèse des constats par domaine

| Domaine (Annexe A) | Maturité moyenne | Constat principal |
| --- | --- | --- |
| A.5 — Mesures organisationnelles (37 mesures) | 2,4 / 4 | PSSI formalisée et approuvée, mais revue des droits d'accès non tracée systématiquement |
| A.6 — Mesures liées aux personnes (8 mesures) | 3,2 / 4 | Formation sécurité à l'intégration et campagnes de sensibilisation effectives |
| A.7 — Mesures physiques (14 mesures) | 3,0 / 4 | Accès aux locaux par badge, salle serveurs sous vidéosurveillance |
| A.8 — Mesures technologiques (34 mesures) | 1,6 / 4 | Secrets d'API en clair, cloisonnement dev/production insuffisant, absence de PCA formalisé |

Le domaine A.8 (mesures technologiques) concentre les écarts les plus critiques, en cohérence avec les risques identifiés lors de l'analyse EBIOS RM.

## 3. Statement of Applicability (extrait)

Échantillon représentatif de mesures évaluées (liste non exhaustive des 93 mesures de l'Annexe A) :

| N° | Mesure | Applicable | Maturité | Justification si non applicable |
| --- | --- | --- | --- | --- |
| A.5.15 | Contrôle d'accès | Oui | 2 | — |
| A.5.18 | Droits d'accès | Oui | 2 | — |
| A.5.29 | Sécurité de l'information en cas de perturbation | Oui | 0 | — |
| A.5.30 | Préparation aux TIC pour la continuité d'activité | Oui | 1 | — |
| A.6.3 | Sensibilisation et formation | Oui | 3 | — |
| A.7.4 | Surveillance physique | Oui | 3 | — |
| A.8.5 | Authentification sécurisée | Oui | 2 | — |
| A.8.9 | Gestion des configurations | Oui | 2 | — |
| A.8.15 | Journalisation | Oui | 2 | — |
| A.8.16 | Surveillance des activités | Oui | 1 | — |
| A.8.20 | Sécurité des réseaux | Oui | 2 | — |
| A.8.24 | Utilisation de la cryptographie | Oui | 1 | — |
| A.8.31 | Séparation des environnements | Oui | 1 | — |
| A.8.34 | Protection des systèmes d'information pendant les tests d'audit | Non | — | Hors périmètre à ce stade (pas d'audit technique externe mené) |

## 4. Détail des écarts

| N° | Mesure ISO 27001 | Constat | Niveau |
| --- | --- | --- | --- |
| NC-01 | A.8.24 — Utilisation de la cryptographie | Les clés d'accès à l'API de paiement sont stockées en clair dans le dépôt de code | **Majeure** |
| NC-02 | A.8.31 — Séparation des environnements | Pas de cloisonnement strict entre environnements de développement et de production | **Majeure** |
| NC-03 | A.5.29 / A.5.30 — Continuité d'activité | Aucun Plan de Continuité d'Activité (PCA) formalisé à ce jour | **Majeure** |
| NC-04 | A.5.18 — Droits d'accès | La revue semestrielle des droits d'accès prévue par la PSSI n'est pas tracée formellement | Mineure |
| NC-05 | A.8.16 — Surveillance des activités | Les journaux d'accès aux comptes clients sont conservés mais non revus régulièrement | Mineure |
| NC-06 | A.8.9 — Gestion des configurations | Absence de procédure formelle de gestion des changements de configuration en production | Mineure |
| NC-07 | A.5.24 — Planification de la gestion des incidents | Procédure de gestion des incidents documentée dans la PSSI mais jamais testée en exercice | Mineure |

Les non-conformités majeures (NC-01, NC-02, NC-03) portent toutes sur des mesures techniques ou organisationnelles essentielles à la protection du service de paiement mobile, et doivent être traitées en priorité avant tout audit de certification externe.

## 5. Plan d'actions correctives

| N° | Action corrective | Priorité | Responsable | Échéance |
| --- | --- | --- | --- | --- |
| NC-01 | Déployer un coffre-fort de secrets (vault) pour les clés d'API | Haute | DSI | T+2 mois |
| NC-02 | Séparer les environnements de développement et de production (réseaux et identifiants distincts) | Haute | DSI | T+2 mois |
| NC-03 | Formaliser un Plan de Continuité d'Activité (PCA) | Haute | RSSI | T+2 mois |
| NC-04 | Mettre en place une revue d'accès tracée (ticket ou registre signé) | Moyenne | RSSI | T+3 mois |
| NC-05 | Définir une procédure de revue périodique des journaux d'accès | Moyenne | Administrateurs système | T+3 mois |
| NC-06 | Formaliser une procédure de gestion des changements | Moyenne | DSI | T+4 mois |
| NC-07 | Organiser un exercice de simulation d'incident (table-top) | Basse | RSSI | T+4 mois |

Un point d'avancement est prévu en comité sécurité à un mois, puis à l'échéance de chaque action.

## 6. Conclusion et recommandation

Le SMSI de NovaPay SARL présente une base solide sur les volets organisationnels, humains et physiques (maturité moyenne ≥ 2,4/4), mais souffre d'écarts significatifs sur le volet technologique (A.8, maturité moyenne 1,6/4), notamment la gestion des secrets, la séparation des environnements, et l'absence d'un Plan de Continuité d'Activité formalisé.

**Recommandation.** Traiter en priorité les trois non-conformités majeures (NC-01, NC-02, NC-03) avant d'engager une démarche de certification externe. Sous réserve de la mise en œuvre effective du plan d'actions correctives, NovaPay pourrait viser un audit de certification ISO/CEI 27001 dans un délai de 6 à 9 mois.

---
*Document rédigé dans un cadre pédagogique (exercice GRC). NovaPay SARL est une entreprise fictive ; aucune donnée réelle n'est concernée.*
