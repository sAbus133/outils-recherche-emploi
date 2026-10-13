# Radar candidatures : guide du membre

Un tableau de bord personnel pour ta recherche d'emploi, piloté avec Claude :

- les offres de LinkedIn, de l'Apec et d'Indeed sont **collectées** automatiquement à partir de tes alertes, **sans doublons** ;
- chaque offre est **classée** A (priorité), B (à examiner) ou C (écartée), selon **tes** critères ;
- tu **suis** tes candidatures : à postuler, postulé, entretien, refus, avec les dates ;
- tu génères en un clic une **lettre de motivation** et un **CV adapté** à l'offre (PDF), à partir de ta base de connaissance : ton CV et ton profil LinkedIn fusionnés, sans rien inventer.

---

## Avant de commencer (5 minutes)

Il te faut :

1. **Claude** avec Cowork (application de bureau ou claude.ai), sur un abonnement qui permet les artifacts et les connecteurs.
2. Le **plugin Radar candidatures** installé (voir ci-dessous).
3. **Gmail** : c'est là qu'arrivent les alertes. Claude te proposera de le connecter.
4. **Google Chrome** avec l'extension **Claude in Chrome**, connectée à ton compte Claude. Elle sert à la tournée de collecte.
5. Tes comptes **LinkedIn** et **Apec** (et **Indeed** si tu l'utilises), ouverts dans Chrome.
6. Ton **CV le plus complet**, en Word ou en PDF.
7. Ton **profil LinkedIn en PDF** : sur LinkedIn, ouvre ton profil, bouton **« Plus »** sous ta photo, puis **« Enregistrer au format PDF »**.

## Installer le plugin (2 minutes)

Dans Claude (Cowork) :
1. Barre latérale : **Personnaliser** (Customize), puis **Plugins**.
2. **Ajouter une marketplace** (Add marketplace), colle : `<compte>/<depot>`
3. Dans la liste qui apparaît, installe **radar-candidatures**.

Dans Claude Code : `/plugin install radar-candidatures --marketplace <compte>/<depot>`

Mises à jour : sur la page Plugins, bouton **Mettre à jour** (Update) de la marketplace.

## Installation guidée (30 à 45 minutes)

Dans une nouvelle conversation Claude, tape :

```
/radar-installation
```

Claude te guide en 7 étapes :

| Étape | Ce qui se passe | Ce que tu fais |
|---|---|---|
| 1. Prérequis | Claude vérifie les outils | Tu réponds, tu connectes Gmail si besoin |
| 2. Documents | Claude lit ton CV et ton profil LinkedIn | Tu joins les deux fichiers |
| 3. Base de connaissance | Claude fusionne les deux et relève les incohérences (dates, intitulés, chiffres) | Tu tranches chaque écart, tu complètes les chiffres manquants |
| 4. Critères | Zone, rayon, salaire plancher, contrat, niveau visé, pistes métier, exclusions | Tu réponds et tu valides |
| 5. Identité du CV | Nom, titre, coordonnées, couleur | Tu choisis |
| 6. Ta page radar | Claude publie ta page personnelle et y enregistre ton profil | Tu l'ouvres, tu vérifies, tu ajoutes ta photo si tu veux (« Mon profil ») |
| 7. Alertes | Claude conçoit tes alertes LinkedIn, Apec et Indeed, et le libellé Gmail « Radar » | Tu crées les alertes et le filtre Gmail en suivant ses indications |

## Dernière étape : lance ta première tournée

À la fin de l'installation, **lance tout de suite ta première tournée** :

1. Ouvre **Google Chrome**, vérifie que tu es connecté à LinkedIn et à l'Apec (et Indeed).
2. Ouvre le **panneau Claude** (icône de l'extension Claude in Chrome).
3. Tape **`/radar`** et valide.

Cette première tournée n'attend pas tes alertes : elle parcourt directement tes recherches sur les **7 derniers jours**, lit chaque offre en entier, la classe et remplit ta page. Compte **15 à 30 minutes**. Si LinkedIn ou l'Apec te demandent de te reconnecter, fais-le toi-même : Claude reprend ensuite.

Ensuite, **une tournée tous les 1 à 3 jours** suffit. Elle lit les nouvelles alertes du libellé « Radar » et ne reprend que les nouveautés.

---

## Au quotidien

**Sur ta page radar**
- Les **nouvelles offres** sont en tête pendant 3 jours, ou jusqu'à ce que tu leur donnes un suivi.
- Donne un **suivi** à chaque offre : À postuler, Postulé (la date du jour s'inscrit), Entretien, Refus, Écartée. Les offres écartées ou refusées disparaissent de la liste ; le menu Suivi permet de les revoir.
- **Lettre** / **CV** : colle le texte complet de l'annonce s'il manque, ajoute des consignes si besoin (« 1 500 caractères max », « insiste sur tel projet »), clique sur **Générer**, relis, puis télécharge le PDF. Chaque version reste enregistrée pour l'offre.
- **+ Ajouter une annonce** : une offre trouvée ailleurs. Colle le lien seul (la prochaine tournée complétera la fiche) ou le texte de l'annonce, et Claude remplit les champs.
- **Mon profil** : ta base de connaissance, tes critères, ta photo. Tu peux corriger directement.

**Les commandes**

| Commande | Où | Pour quoi |
|---|---|---|
| `/radar` | Panneau Claude de Chrome | Tournée de collecte |
| `/radar-profil` | N'importe quelle conversation | Ajouter un chiffre, une mission, une formation ; changer un critère |
| `/radar-alertes` | N'importe quelle conversation | Revoir ou resserrer tes alertes |

**Astuce** : un contact t'envoie une offre par mail ? Range ce mail dans le libellé Gmail « Radar » : la prochaine tournée l'ajoutera, même hors de tes critères.

## Règles d'or

- **Relis toujours** la lettre et le CV avant d'envoyer. Claude ne s'appuie que sur ta base. Si ta base est pauvre, les documents le seront aussi : enrichis-la avec `/radar-profil`.
- **Rien n'est inventé.** Si une offre demande ce que ta base ne montre pas, Claude ne le prétend pas. Les « points d'attention » affichés sous la lettre sont pour toi seul : ils ne sont ni copiés ni téléchargés.
- **Les noms de fichiers restent sobres** : `CV_Prenom_Nom_Intitule.pdf`, sans trace d'outil.

## Confidentialité et précautions

- Ta page radar est **privée** : elle contient ton parcours, tes coordonnées et tes candidatures. **Ne partage pas son lien.**
- Les lettres et les CV sont rédigés par Claude à partir de ta base, dans ton compte.
- Tes données restent dans ton compte Claude et dans ta page. L'association n'y a pas accès.
- La tournée navigue sur LinkedIn, l'Apec et Indeed **avec tes propres sessions**, à un rythme d'usage personnel. Ces sites encadrent la navigation automatisée dans leurs conditions d'utilisation : tu restes responsable de l'usage de tes comptes. Claude ne saisit jamais de mot de passe, ne résout pas de captcha, ne postule pas et n'envoie aucun message à ta place.

## En cas de souci

| Problème | Solution |
|---|---|
| `/radar` dit que Chrome n'est pas joignable | Lance la tournée depuis le **panneau Claude de Chrome**, pas depuis l'application de bureau |
| La page affiche « Ton radar n'est pas encore configuré » | Relance `/radar-installation` (Claude réutilise ta page existante) |
| La génération ne marche pas | Ouvre la page sur claude.ai (pas dans un aperçu) et reconnecte-toi |
| Trop d'offres hors sujet | `/radar-alertes` pour resserrer les alertes ; `/radar-profil` pour préciser tes règles de rang |
| Aucune nouvelle offre | Vérifie que les mails d'alerte arrivent bien sous le libellé « Radar » dans Gmail |

---

*Pour l'animateur ou l'animatrice : le plugin ne contient aucune donnée personnelle. Chaque membre crée sa propre page lors de l'installation. Pour une mise à jour, publie une nouvelle version dans le dépôt (numéro de version augmenté dans `plugin.json`). Chaque membre clique sur « Mettre à jour » dans ses plugins, puis relance `/radar-installation` et choisit « Mettre à jour la page seulement » : la page est republiée à la même adresse et garde toutes ses données.*
