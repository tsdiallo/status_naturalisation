# Statut API du Dossier Naturalisation

Extension Chrome (Manifest V3) qui superpose un **suivi visuel détaillé** de votre
demande de naturalisation directement sur le portail **ANEF**
(`administration-etrangers-en-france.interieur.gouv.fr`).

L'extension lit l'état de votre dossier via l'API du portail (avec votre session déjà
connectée), traduit le code de statut technique en langage clair, et affiche une
frise de progression par grandes phases (Préfecture → SDANF & SCEC → Décret → Cérémonie).

> ⚠️ Projet communautaire non officiel. Aucune affiliation avec le Ministère de l'Intérieur.

## Fonctionnalités

- **Frise de progression** par macro-phases avec pourcentage d'avancement.
- **Statut en clair** : traduction de plus de 60 codes de statut techniques.
- **Dates clés** : dépôt de la demande, récépissé de complétude, entretien
  d'assimilation, numéro de décret.
- **Durées entre étapes** pour visualiser le temps passé à chaque phase.
- **Estimation des délais** *(nouveau en v3.9.0)* : ancienneté du dossier, temps passé
  dans le statut actuel et échéance légale indicative (récépissé de complétude + 18 mois)
  avec le temps restant.
- **Historique des changements de statut** *(nouveau en v3.7.0)* : chaque nouveau
  statut détecté lors de vos visites est enregistré localement et affiché sous forme
  de frise chronologique.
- **Résumé copiable** *(nouveau en v3.7.0)* : un bouton copie un résumé texte de votre
  dossier (statut, dates, historique) — pratique pour le partager sur les forums d'entraide.
- **Alertes « action requise »** *(nouveau en v3.8.0)* : un encart met en évidence les
  statuts critiques (mise en demeure, compléments demandés, RAPO, décision défavorable
  ou irrecevabilité en délai de recours, classement sans suite) avec un conseil d'action,
  ainsi que les bonnes nouvelles (décret publié).
- **Étape actuelle / étape suivante** *(nouveau en v4.0.0)* : explication en langage
  clair de ce qui se passe maintenant et de ce qui vient après.
- **Export JSON** de l'historique et **ajout de l'entretien au calendrier** (fichier
  `.ics` avec rappel J-1) *(nouveau en v4.0.0)*.
- **Masquage des données sensibles** (numéro de série, timbre fiscal) avec bouton
  afficher/masquer.

## Confidentialité

- L'extension ne s'active **que** sur le domaine du portail ANEF
  (`host_permissions` limité à ce seul domaine).
- Aucune donnée n'est envoyée vers un serveur tiers. Les appels réseau visent
  uniquement l'API officielle du portail, avec votre session.
- L'historique des statuts est stocké **localement** dans le `localStorage` de votre
  navigateur (clé `anfExtensionStatusHistory:<idDossier>`). Vous pouvez l'effacer en
  vidant les données de site du portail.

## Installation

Vidéo tutorielle sur YouTube (je ne suis pas le propriétaire des chaînes) :

- FR : <https://www.youtube.com/watch?v=WhW91uf_bVI>
- AR : <https://www.youtube.com/watch?v=vaitOnjyNFQ>

1. Télécharger le [fichier ZIP](https://github.com/divisi0n/status_naturalisation/releases),
   puis décompressez-le pour obtenir le dossier.
2. Rendez-vous sur `chrome://extensions`.
3. En haut à droite, activez le **Mode Développeur**.

   ![Mode développeur](https://github.com/user-attachments/assets/1c26f75b-963f-473b-a898-0c44e82eba9e)

4. En haut à gauche, cliquez sur **Charger l'extension non empaquetée** puis
   sélectionnez votre dossier d'extension.

   ![Charger l'extension](https://github.com/user-attachments/assets/6f13ef5b-e365-449d-94f1-d541449855c5)

Et voilà, l'extension est installée et utilisable sur votre Chrome 🎉

<img width="1296" height="448" alt="Aperçu" src="https://github.com/user-attachments/assets/128a2754-ded0-4abb-8e8e-ef61e9ebc57d" />

## Utilisation

1. Connectez-vous au portail ANEF.
2. La frise de progression apparaît automatiquement sous l'en-tête du site.
3. Le panneau **Suivi & historique** se trouve juste en dessous : utilisez
   **Copier le résumé** pour récupérer un récapitulatif texte, ou **Masquer** pour le replier.
4. Pour le diagnostic, ouvrez la console développeur (`F12`) et tapez `__ANF_API_INFOS__`
   pour voir toutes les informations extraites.

## Solution alternative : ANEF Status Tracker

[Installer depuis le Chrome Web Store](https://chromewebstore.google.com/detail/anef-status-tracker/icnpklneeaiffilemaflccdejefpehek)
— installation en un clic, mises à jour automatiques
(source : <https://github.com/Letranger-dev/anef-extension>).

## Développement

L'essentiel de la logique se trouve dans `content.js` (injecté dans la page via
`inject.js`). `forge.min.js` fournit le déchiffrement RSA du code de statut.

Vérifier la syntaxe avant de publier :

```bash
node --check content.js
```

Pensez à incrémenter la version dans `manifest.json` **et** dans `content.js`
(`extensionVersion`) à chaque release. Voir [`CHANGELOG.md`](CHANGELOG.md).
