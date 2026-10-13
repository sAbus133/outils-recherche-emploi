# Journal des versions

## radar-candidatures 1.0.0 (octobre 2026)
- Installation guidée en 7 étapes (`/radar-installation`) : CV + profil LinkedIn fusionnés, contrôle de cohérence, critères, page personnelle.
- Aide aux alertes LinkedIn, Apec, Indeed et au libellé Gmail « Radar » (`/radar-alertes`).
- Tournée de collecte (`/radar`), avec mode démarrage sur 7 jours sans attendre les alertes.
- Enrichissement de la base en conversation (`/radar-profil`).

## Publier une nouvelle version
1. Modifier les fichiers du plugin.
2. Augmenter `version` dans `plugins/radar-candidatures/.claude-plugin/plugin.json` (sinon les membres ne reçoivent pas la mise à jour).
3. Ajouter une entrée ici, valider (`claude plugin validate .`), commit, push.
