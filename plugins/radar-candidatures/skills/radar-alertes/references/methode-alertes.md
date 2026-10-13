# Méthode de recherche et d'alertes : syntaxe par site

Retour d'expérience terrain (octobre 2026). Les sites changent : en cas d'écart, se fier à ce que le membre voit à l'écran.

## Principes

1. **Familles d'intitulés, pas mots vagues.** « directeur financier » ramène des DAF ; « finance » ramène tout.
2. **Une alerte par piste métier**, pas une alerte fourre-tout.
3. **Toujours trier par date** et limiter à la fraîcheur utile.
4. **Un filet large par site quand c'est possible** : filtre de fonction ou de catégorie, sans mots-clés, borné par la zone et le salaire.
5. **Évaluer après une semaine** : une alerte qui ramène surtout du bruit se resserre ; une alerte muette s'élargit.

## LinkedIn

- Opérateurs : `OR`, `AND`, `NOT` en **majuscules**, guillemets pour les expressions, parenthèses acceptées.
  Exemple : `"directeur financier" OR DAF OR "responsable administratif et financier" OR CFO`
- URL de résultats (format à utiliser) :
  `https://www.linkedin.com/jobs/search-results/?keywords=<requête encodée>&location=<ville>&distance=<miles>&sortBy=DD`
  - `distance` est en **miles** (25 ≈ 40 km, 50 ≈ 80 km).
  - Fraîcheur : `f_TPR=r<secondes>` (`r86400` = 24 h, `r604800` = 7 jours).
  - Salaire (si proposé dans la zone) : filtre « Salaire » de l'interface, paramètre `f_SAL`.
- Ne jamais utiliser l'ancien format `/jobs/search/?keywords=` : la page reste bloquée au chargement.
- Lien direct d'une offre : `https://www.linkedin.com/jobs/view/<jobId>/`. Sur la page de résultats, cliquer une carte affiche `currentJobId=<jobId>` dans l'URL.
- Les mails d'alerte sont **tronqués** (6 offres environ) : la liste complète se lit via « Voir toutes les offres ».
- Alerte : interrupteur « Créer une alerte » en haut des résultats ; fréquence quotidienne, par e-mail.

## Indeed

- Opérateurs : `or` entre parenthèses, guillemets : `("directeur financier" or daf or raf)`.
- URL : `https://fr.indeed.com/emplois?q=<requête>&l=<ville>&radius=<km>&sort=date&fromage=<jours>`
- Lien d'une offre : `https://fr.indeed.com/viewjob?jk=<jk>`.
- Alerte : « Recevoir les nouvelles offres par e-mail ».

## Apec

- **Pas de OR** : `"a" OR "b"` casse les guillemets et ramène du bruit (direction d'usine, comptabilité, etc.). Une alerte = une expression entre guillemets.
- **La virgule vaut ET** : `"directeur financier", industrie` exige les deux.
- **5 recherches / alertes enregistrées au maximum.** Répartition conseillée : 3 ou 4 expressions + 1 filet large.
- **Filet large** : aucun mot-clé, filtre **Fonction** du métier (sélection dans l'interface ; exemple : Fonction « Informatique » = `fonctions=101833`), + lieu + rayon + salaire minimum.
- Préciser un **rayon** autour de la ville (`distance=…`), sinon la recherche se limite à la ville.
- URL type :
  `https://www.apec.fr/candidat/recherche-emploi.html/emploi?motsCles=<expression>&lieux=<code lieu>&distance=<km>&salaireMinimum=<k€>&salaireMaximum=200&sortsType=DATE`
  - `lieux` est un code interne : le récupérer en faisant la recherche une fois dans l'interface, puis en lisant l'URL.
  - Les codes de fonction et de statut se récupèrent de la même façon.
- Lien d'une offre : `https://www.apec.fr/candidat/recherche-emploi.html/emploi/detail-offre/<id>`.
- Vérifier chaque alerte dans « Mes alertes » après création.

## Autres sources utiles aux cadres

- **France Travail** (alertes par e-mail, utile pour les postes publics et PME).
- **Welcome to the Jungle**, **Cadremploi**, sites carrières des grands groupes de la zone.
- **Cabinets de recrutement** du secteur : leurs mails peuvent être rangés à la main dans « Radar ».
Ces sources sont facultatives : la tournée sait traiter tout mail du libellé Radar qui contient un lien d'offre.

## Gmail

- Libellé unique : **Radar**.
- Filtre : expéditeurs des alertes emploi uniquement (pas les notifications sociales LinkedIn).
- La tournée lit `label:Radar after:<horodatage>` : la date de **réception** compte, pas la date d'étiquetage.
