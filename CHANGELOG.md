# Changelog

Toutes les évolutions notables de l'extension sont documentées ici.
Le format s'inspire de [Keep a Changelog](https://keepachangelog.com/fr/1.0.0/).

## [4.0.0]

### Ajouté
- **Carte « Étape actuelle / étape suivante »** : explication en langage clair de ce
  qui se passe à l'étape en cours (mini-glossaire des 13 étapes) et aperçu de l'étape
  qui vient après. Reprise dans le résumé copiable.
- **Chips d'informations** : n° de dossier, code technique du statut, date d'entretien,
  plateforme, n° de décret, visibles d'un coup d'œil en tête du panneau.
- **Export JSON** de l'historique et des informations du dossier (sauvegarde locale
  avant un éventuel vidage des données de site).
- **Entretien → calendrier** : téléchargement d'un fichier `.ics` (avec rappel J-1)
  quand une date d'entretien d'assimilation à venir est détectée.

### Modifié
- Polissage du panneau : effets de survol sur les cartes métriques et la frise
  chronologique, disposition responsive de la carte d'étape.

## [3.9.0]

### Ajouté
- **Estimation des délais** : le panneau de suivi affiche désormais l'ancienneté du
  dossier, le temps passé dans le statut actuel et une échéance légale indicative
  (récépissé de complétude + 18 mois) avec le temps restant ou le dépassement. Ces
  métriques sont également reprises dans le résumé copiable. Un avertissement rappelle
  le caractère indicatif et la variabilité selon les préfectures.

## [3.8.0]

### Ajouté
- **Alertes « action requise »** : un encart contextuel met en évidence les statuts
  critiques (mise en demeure, compléments demandés, RAPO, décision défavorable ou
  irrecevabilité en délai de recours, classement sans suite) avec un conseil
  d'action, ainsi que les bonnes nouvelles (décret publié, demande finalisée).
  Quatre niveaux de couleur : action (rouge), vigilance (orange), info (bleu),
  succès (vert). L'alerte est aussi reprise dans le résumé copiable.

## [3.7.0]

### Ajouté
- **Historique des changements de statut** : chaque nouveau statut détecté est
  enregistré localement (`localStorage`) et affiché sous forme de frise chronologique,
  avec la durée écoulée entre chaque étape.
- **Résumé copiable** : bouton « Copier le résumé » qui place dans le presse-papiers
  un récapitulatif texte du dossier (statut, dates clés, historique).
- Bouton « Masquer / Afficher » pour replier le panneau de suivi.

### Modifié
- Description du `manifest.json` plus explicite.
- README réécrit (fonctionnalités, confidentialité, utilisation, développement).

## [3.6.1]
- Mode « retry » sur les appels API.
- Gestion de l'authentification et des réessais API.

## [3.6.0] et antérieurs
- Nouvelle version ANEF (refonte de la frise de progression).
- Corrections d'affichage et d'image.
- Traduction étendue des codes de statut (Préfecture, SDANF, SCEC, Décret, CSS…).
