# Carnet de bord — ML Engineer

> Suivi de progression. Ce fichier est à la racine du dossier `ML-Engineer/`.
> Mis à jour après chaque séance : remplace l'ancienne version par la nouvelle.

Dernière mise à jour : 25 septembre 2026

---

## Profil, matériel et règles

**Élève** : dev full-stack, licence MIAGE (2024), vise ML Engineer spécialisé en vision médicale pour l'ophtalmologie. Programme de référence : `00-index.md`.

**Matériel** : PC portable Hasee, RTX 3070 Mobile 8 Go de VRAM, sous Parrot OS (Python 3.13.5).

**État du GPU (25/09/2026)** : graphiques hybrides (Intel UHD 730 pour l'affichage + RTX 3070 Mobile). Pilote libre `nouveau` chargé, sans CUDA. Démarrage UEFI, Secure Boot désactivé. À faire avant la phase 2 : installer le pilote propriétaire NVIDIA avec un guide dédié.

**Capacités** : suffisant pour tout le programme et pour fine-tuner des modèles de petite taille (ResNet, EfficientNet, petits ViT). Les gros modèles passeront par Colab ou Kaggle, ou par la quantification.

**Règles de la classe**
- Niveau d'exigence : élevé. Un module est validé à 80 % au quiz ; en dessous, on retravaille les points faibles.
- Langue : français, termes techniques en anglais.
- Séance type : récap actif du cours précédent, cours, exercices (maths et code), quiz.
- Blocage : indices d'abord, solution complète après deux vraies tentatives.
- Devoirs faits avant la séance suivante, sinon pas de nouveau cours.
- Horaires libres, avec un minimum de 5 séances par semaine.

---

## Progression

**Prochaine étape** : lire le corrigé du module 01, refaire E9 soi-même, puis passer le quiz du module 01 (80 % requis).

| Module | Phase | Statut | Quiz (%) |
|--------|-------|--------|----------|
| 00. Diagnostic | 0 | Non passé : niveau zéro déclaré | — |
| 01. Environnement de travail | 0 | Exercices corrigés, quiz à passer | — |
| 02. Types, variables et modèle objet | 0 | À faire | — |
| 03. Contrôle du flux et fonctions | 0 | À faire | — |
| 04. Structures de données | 0 | À faire | — |
| 05. Chaînes, fichiers, exceptions | 0 | À faire | — |
| 06. Modules, packages, stdlib | 0 | À faire | — |
| 07. Programmation orientée objet | 0 | À faire | — |
| 08. Python avancé | 0 | À faire | — |
| 09. Code professionnel | 0 | À faire | — |
| 10. Projet de phase 0 | 0 | À faire | — |
| Phase 1 — Fondations (12 modules) | 1 | À venir | — |
| Phase 2 — Deep learning pour la vision | 2 | À venir | — |
| Phase 3 — IA pour l'ophtalmologie | 3 | À venir | — |
| Phase 4 — Mise en production | 4 | À venir | — |

Le détail des modules des phases 1 à 4 sera ajouté au démarrage de chaque phase.

---

## Points faibles à retravailler

**Niveau déclaré : débutant en Python, en maths et en ML.** Les notions du lycée sont en grande partie oubliées. L'expérience en développement (logique, terminal, autre langage) reste un atout.

Conséquences sur les cours :
- Ajout d'une phase 0 dédiée à Python, du niveau débutant jusqu'au fonctionnement interne.
- Chaque notion est reprise depuis la base : définition, intuition, exemple chiffré, sous le capot, puis application au ML.
- Plus d'exemples résolus pas à pas avant les exercices.
- Exercices gradués : échauffement → application → problème de type ML.
- Chaque cours indexe la documentation officielle et des ressources pour approfondir.
- Calendrier décalé d'un mois : fin du programme prévue en octobre 2027.

Détail par notion (mis à jour au fil des modules) :

| Date | Point faible | Constaté dans | Action |
|------|--------------|---------------|--------|
| 25/09/2026 | Confusion entre environnement virtuel, interpréteur et kernel Jupyter | Module 01, Q4 | Retravaillé dans le quiz 01 et le module 02 |
| 25/09/2026 | Idée reçue : « un venv est une machine virtuelle » | Module 01, Q1 | Corrigé ; à vérifier au quiz |
| 25/09/2026 | Ne lit pas les messages d'erreur en entier (`desactivate` au lieu de `deactivate`) | Module 01 | Réflexe à construire : lire l'erreur avant de demander |
| 25/09/2026 | Répond « je ne trouve pas » sans relire le cours (E3, E6) | Module 01 | Relire la section concernée avant d'abandonner |
| 25/09/2026 | Réponses incomplètes : ne répond pas à toutes les sous-questions (E2, E6) | Module 01 | Relire l'énoncé avant d'envoyer |

---

## Historique des séances

| Date | Séance | Résultat | Devoirs |
|------|--------|----------|---------|
| 24/09/2026 | Cadrage : spécialisation, programme, règles, organisation des fichiers | Spécialité choisie (ophtalmologie), programme et règles fixés, phase 0 Python ajoutée | Créer le dossier `ML-Engineer/` |
| 24/09/2026 | Diagnostic non passé ; départ au niveau zéro | Module 01 envoyé | Exercices E1–E11 et Q1–Q4 du module 01, dépôt GitHub |
| 25/09/2026 | Correction du module 01 | Manipulations réussies (E1, E4, E5, E7, E8, E10, Q2). Q1 et Q4 faux après 2 tentatives. E9 non tenté, E2, E3, E6 incomplets : corrigé donné à la demande de l'élève, sans 2e tentative. GPU diagnostiqué. | Lire le corrigé, refaire E9, nettoyer `phase-1-fondations/` sur GitHub, passer le quiz 01 |
