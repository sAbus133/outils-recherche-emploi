# Journal des versions

## radar-candidatures 1.2.0 (novembre 2026)
- **Garde-fou de positionnement** : deux angles au plus, un seul par lettre ou CV, pour qu'un recruteur comprenne en 12 secondes ce que tu vends. Une offre hors positionnement perd un rang.
- **Métiers de cœur** : ces postes ne sont jamais écartés mécaniquement.
- **Voie freelance** (facultative) : missions classées selon tes seuils de TJM, et bouton **Dossier** qui produit un dossier de mission en PDF, avec ses propres consignes par offre.
- **Lettres** : plus aucun manque annoncé. L'écart reste dans les « points d'attention », et la lettre apporte la preuve d'un défi nouveau déjà relevé.
- **Tournée** : recherches directes sur l'Apec et Indeed à chaque passage, Free-Work si tu le retiens (métiers de la tech et de l'IT), rapprochement des offres republiées par les cabinets, collecte LinkedIn plus fiable.
- **Page** : le sous-titre affiche la date de la dernière mise à jour et le nombre de nouvelles offres.
- **Correctif** : la réduction d'une lettre à une limite de caractères utilise le modèle standard.

**À faire après la mise à jour** : `/radar-installation` › « Mettre à jour la page seulement » (tes données sont conservées), puis `/radar-profil` pour renseigner tes positionnements, tes métiers de cœur et la voie freelance, et `/radar-alertes` pour enregistrer les recherches directes. Sans ces réglages, la page et la tournée continuent de fonctionner, sans garde-fou ni dossier de mission. Les offres déjà présentes ne sont pas reclassées.

## radar-candidatures 1.1.0 (octobre 2026)
- Lettre modifiable directement dans la fenêtre d'affichage avant l'export PDF, enregistrée automatiquement, avec le nombre de caractères.
- Consignes séparées pour la lettre et pour le CV, mémorisées par offre : une consigne de lettre n'influence plus le CV.

## radar-candidatures 1.0.0 (octobre 2026)
- Installation guidée en 7 étapes (`/radar-installation`) : CV + profil LinkedIn fusionnés, contrôle de cohérence, critères, page personnelle.
- Aide aux alertes LinkedIn, Apec, Indeed et au libellé Gmail « Radar » (`/radar-alertes`).
- Tournée de collecte (`/radar`), avec mode démarrage sur 7 jours sans attendre les alertes.
- Enrichissement de la base en conversation (`/radar-profil`).

## Publier une nouvelle version
1. Modifier les fichiers du plugin.
2. Augmenter `version` dans `plugins/radar-candidatures/.claude-plugin/plugin.json` (sinon les membres ne reçoivent pas la mise à jour).
3. Ajouter une entrée ici, valider (`claude plugin validate .`), commit, push.
