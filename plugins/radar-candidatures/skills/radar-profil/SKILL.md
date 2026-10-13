---
name: radar-profil
description: Compléter ou corriger la base de connaissance et les critères du Radar candidatures en conversation (nouveau chiffre, mission oubliée, formation, changement de zone ou de salaire). À lancer avec /radar-profil.
---

# /radar-profil

La base de connaissance (`profil/main` de la page radar) est la **seule** source des lettres et des CV. Cette commande sert à l'enrichir ou à la corriger, proprement, sans rien inventer.

## Déroulé

1. **Trouver la page** : `Artifact` action `list`, artifact « Radar candidatures » (demander lequel s'il y en a plusieurs ; aucun → `/radar-installation`).
2. **Lire** `profil/main` avec `ArtifactData` `get` et noter sa version.
3. **Recueillir** ce que le membre veut ajouter ou changer. S'il ne sait pas quoi ajouter, l'aider avec des questions ciblées sur les points faibles visibles dans la base :
   - résultats non chiffrés ;
   - périmètre (budget, équipe, nombre de sites) absent ;
   - outils cités sans contexte ;
   - trous de dates ;
   - compétence revendiquée sans preuve.
   - Une question à la fois, trois au plus par échange.
4. **Classer** chaque information :
   - **Complément** (fait nouveau qui précise une expérience existante) → une ligne dans `ajouts`, au format `- [Entreprise ou rubrique] fait précis (ajouté le JJ/MM/AAAA)`.
   - **Correction** (un fait de `source` est faux : date, intitulé, chiffre) → modifier `source` à l'endroit exact. Montrer au membre l'avant et l'après.
   - **Nouvelle expérience, formation, certification** → l'insérer dans `source`, à sa place chronologique, au format existant.
   - **Critère de recherche** (zone, salaire, contrat, niveau, exclusion, règle de rang) → modifier `criteres` ; si les pistes ou les villes proches changent, mettre à jour `pistes` ou `local`. Prévenir : changer les pistes ne reclasse pas les offres déjà présentes.
5. **Refuser poliment** ce qui n'a pas sa place :
   - données sensibles inutiles au recrutement (santé, situation familiale, numéro de sécurité sociale, âge) ;
   - embellissement non étayé (« mets que j'ai managé 20 personnes » alors que la base dit 5) : le dire franchement et proposer une formulation exacte et valorisante.
6. **Écrire** : `ArtifactData` `update` sur `profil/main` avec `if_version`, uniquement sur les champs modifiés, plus `updatedAt` (ISO 8601 UTC avec `Z`). En cas de conflit de version, relire, fusionner, réécrire.
7. **Confirmer** en une ou deux lignes ce qui a changé. Rappeler que les prochaines lettres et les prochains CV en tiendront compte. Les documents déjà générés ne changent pas : il faut cliquer « Générer » à nouveau.

## Règles

- Rien n'entre dans la base qui ne vienne du membre ou de ses documents.
- Ne jamais supprimer une expérience sans demande explicite.
- Le membre peut aussi tout modifier lui-même via le bouton « Mon profil » de la page.
