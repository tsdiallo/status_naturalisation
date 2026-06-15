# Changelog

Toutes les évolutions notables de l'extension sont documentées ici.
Le format s'inspire de [Keep a Changelog](https://keepachangelog.com/fr/1.0.0/).

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
