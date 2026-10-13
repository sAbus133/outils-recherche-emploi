---
name: radar-alertes
description: Aide à créer ou revoir les alertes emploi (LinkedIn, Apec, Indeed) et le libellé Gmail « Radar » qui alimentent le Radar candidatures, à partir des critères du membre. À lancer avec /radar-alertes, ou enchaîné en fin d'installation.
---

# /radar-alertes

Objectif : que chaque offre pertinente arrive dans Gmail sous le libellé **Radar**, sans noyer le membre sous le bruit. Les recherches validées sont aussi enregistrées dans la page radar (`meta/recherches`) pour la première tournée.

Méthode détaillée et syntaxe par site : `references/methode-alertes.md`. Lis-la avant de proposer des recherches.

## Étape A · Charger le contexte

1. Trouver la page radar du membre : `Artifact` action `list`, artifact intitulé « Radar candidatures ». S'il y en a plusieurs, demander lequel. S'il n'y en a pas, proposer `/radar-installation` et s'arrêter.
2. `ArtifactData` `get` sur `profil/main` : lire `criteres`, `pistes`, `local`, `ville`, et le titre. Lire aussi `meta/recherches` s'il existe (révision d'alertes existantes).

## Étape B · Concevoir les recherches

Pour chaque piste métier, construire **une famille d'intitulés** : 3 à 6 intitulés réellement utilisés par les recruteurs pour ce poste et ce niveau, en français, et en anglais si c'est l'usage du secteur. Exemple pour une piste « Direction financière » : « directeur financier », « DAF », « responsable administratif et financier », « CFO ».

Puis décliner par site selon `references/methode-alertes.md` :
- **LinkedIn** : une alerte par piste, intitulés reliés par `OR` (en majuscules), expressions entre guillemets ; zone = ville de référence + rayon ; tri par date.
- **Indeed** : même logique (`or` accepté), ville + rayon.
- **Apec** : **pas de OR** (il casse les guillemets et ramène du bruit). Une alerte = une expression entre guillemets. La virgule vaut **ET**. Limite : **5 alertes maximum** sur l'Apec. Donc :
  - 3 ou 4 alertes sur les intitulés les plus porteurs (une expression chacune) ;
  - 1 alerte « **filet large** » : aucun mot-clé, filtre **Fonction** correspondant au métier du membre + zone + rayon + salaire minimum. Elle rattrape les intitulés imprévus.
- Filtres communs : salaire plancher quand le site le permet, contrat (CDI ou autre selon critères), tri par date, rayon cohérent avec la zone.

Présente au membre un **tableau** : site · nom de l'alerte · requête exacte · zone/rayon · filtres. Explique en une ligne le rôle du filet large. Fais valider ou corriger.

## Étape C · Créer les alertes

Par défaut, guide le membre pas à pas, site par site (il clique, toi tu donnes l'URL de recherche préremplie et le geste exact) :
- **LinkedIn** : ouvrir l'URL de recherche, vérifier les résultats, activer l'interrupteur **« Créer une alerte »** / « Alerte emploi » en haut de la liste ; fréquence **quotidienne**, réception **par e-mail**.
- **Indeed** : ouvrir l'URL, cliquer **« Recevoir les nouvelles offres par e-mail »** (ou l'icône d'alerte), confirmer l'adresse Gmail.
- **Apec** : ouvrir l'URL, cliquer **« Créer une alerte »** / « Enregistrer cette recherche », activer l'envoi par e-mail. Vérifier ensuite dans **Mon espace › Mes alertes** que chaque alerte existe bien (une alerte peut ne pas s'enregistrer si la fenêtre ne s'est pas ouverte).

Si le membre te demande de les créer toi-même **et** que Claude in Chrome est joignable : annonce la liste exacte des alertes à créer et attends un **oui explicite** (ce sont des réglages durables de ses comptes). Crée-les une par une, puis contrôle la page de gestion des alertes de chaque site et signale toute alerte manquante. Ne jamais saisir de mot de passe ; si une connexion est demandée, le membre se connecte lui-même.

## Étape D · Gmail : libellé « Radar » et filtre

1. Si Gmail n'est pas connecté : proposer de le connecter (`SuggestConnectors`). Sans Gmail, la tournée ne fonctionne qu'en mode recherche directe.
2. **Libellé** : vérifier avec `list_labels` si « Radar » existe. Sinon, proposer de le créer (`create_label`) et le créer sur un oui.
3. **Identifier les expéditeurs réels** : chercher les alertes déjà reçues (`search_threads`, par exemple `from:linkedin.com newer_than:30d`, `from:indeed newer_than:30d`, `from:apec newer_than:30d`) et relever l'adresse exacte des mails d'alerte emploi (pas les notifications sociales ni les newsletters). Si aucune alerte n'est encore arrivée, partir de :
   `from:(jobalerts-noreply@linkedin.com OR indeed.com OR apec.fr)` et prévenir qu'il faudra ajuster après les premiers envois.
4. **Filtre** : le connecteur Gmail ne crée pas de filtres. Guide le membre dans Gmail :
   - coller la requête dans la barre de recherche ;
   - ouvrir les options de recherche (icône à droite), puis **« Créer un filtre »** ;
   - cocher **« Appliquer le libellé : Radar »** ;
   - ne **pas** cocher « Ignorer la boîte de réception » si le membre veut continuer à voir les alertes ;
   - cocher « Appliquer également le filtre aux conversations correspondantes » ;
   - Créer.
5. Préciser que le membre peut aussi **ranger à la main** dans « Radar » une offre reçue autrement (mail d'un contact, cabinet) : la tournée la traitera.

## Étape E · Enregistrer les recherches dans la page

`ArtifactData` `set` sur `meta/recherches` :
```json
{"liste": [{"site": "LinkedIn", "libelle": "Direction financière", "url": "<URL de recherche propre, triée par date>", "alerte": true}],
 "requeteGmail": "<requête du filtre>",
 "updatedAt": "<ISO 8601 UTC avec Z>"}
```
Les URL sont celles des **pages de résultats**, sans paramètres de suivi. Pour LinkedIn, le format `https://www.linkedin.com/jobs/search-results/?keywords=…` (jamais `jobs/search/?keywords=`).

## Étape F · Conclure

- Résumer : nombre d'alertes par site, filet large, libellé et filtre Gmail.
- Prévenir que les premiers mails d'alerte arrivent sous 24 h.
- Si l'on vient de `/radar-installation`, rendre la main à l'installation pour l'invitation à la première tournée. Sinon, rappeler que `/radar` se lance depuis le panneau Claude de Chrome.

## Règles

- Peu d'alertes précises valent mieux que beaucoup d'alertes bruyantes. Si une alerte ramène plus de 50 % de hors-sujet après une semaine, la resserrer.
- Ne jamais créer, modifier ou supprimer une alerte ou un filtre sans accord explicite.
- Ne pas promettre de limites ou de fonctions de sites non vérifiées : si un bouton a changé de nom, demander au membre ce qu'il voit.
