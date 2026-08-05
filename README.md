# Statut API du Dossier Naturalisation

Extension Chrome (Manifest V3) qui superpose un **suivi visuel détaillé** de votre
demande de naturalisation directement sur le portail **ANEF**
(`administration-etrangers-en-france.interieur.gouv.fr`).

L'extension lit l'état de votre dossier via l'API du portail (avec votre session déjà
connectée), traduit le code de statut technique en langage clair, et affiche une
frise de progression par grandes phases (Préfecture → SDANF & SCEC → Décret → Cérémonie),
complétée par un panneau **Suivi & historique**.

> ⚠️ Projet communautaire non officiel. Aucune affiliation avec le Ministère de l'Intérieur.

## Fonctionnalités

### Frise de progression

- **Progression par macro-phases** (Préfecture, puis SDANF & SCEC) avec pourcentage
  d'avancement global.
- **Statut en clair** : traduction de plus de 60 codes de statut techniques.
- **Dates clés** : dépôt de la demande, récépissé de complétude, entretien
  d'assimilation, numéro de décret.
- **Durées entre étapes** pour visualiser le temps passé à chaque phase.

### Panneau « Suivi & historique »

- **Alertes « action requise »** : un encart met en évidence les statuts critiques
  (mise en demeure, compléments demandés, RAPO, décision défavorable ou irrecevabilité
  en délai de recours, classement sans suite) avec un conseil d'action, ainsi que les
  bonnes nouvelles (décret publié). Quatre niveaux visuels : action (rouge),
  vigilance (orange), info (bleu), succès (vert).
- **Chips d'informations** : n° de dossier, code technique du statut, date d'entretien,
  plateforme d'instruction et n° de décret, visibles d'un coup d'œil.
- **Étape actuelle / étape suivante** : explication en langage clair de ce qui se passe
  maintenant (mini-glossaire des 13 étapes) et aperçu de l'étape qui vient après.
- **Estimation des délais** : ancienneté du dossier, temps passé dans le statut actuel
  et échéance légale indicative (récépissé de complétude + 18 mois) avec le temps
  restant — estimation indicative, les délais réels variant selon les préfectures.
- **Historique des changements de statut** : chaque nouveau statut détecté lors de vos
  visites est enregistré localement et affiché en frise chronologique, avec la durée
  écoulée entre chaque changement.

### Exports et partage

- **Copier le résumé** : récapitulatif texte complet du dossier (statut, alerte, étape,
  métriques, dates clés, historique) dans le presse-papiers — pratique pour les forums
  d'entraide.
- **Exporter JSON** : sauvegarde de l'historique et des informations du dossier dans un
  fichier téléchargé (utile avant de vider les données de site).
- **Entretien → calendrier** : quand une date d'entretien d'assimilation à venir est
  détectée, téléchargement d'un fichier `.ics` (avec rappel la veille) à ouvrir dans
  Google Calendar, Outlook, etc.

### Vie privée à l'écran

- **Masquage des données sensibles** (numéro de série, timbre fiscal) avec bouton
  afficher/masquer.

L'historique détaillé des versions est dans le [`CHANGELOG.md`](CHANGELOG.md).

## Confidentialité

- L'extension ne s'active **que** sur le domaine du portail ANEF
  (`host_permissions` limité à ce seul domaine).
- Aucune donnée n'est envoyée vers un serveur tiers. Les appels réseau visent
  uniquement l'API officielle du portail, avec votre session. Les exports (résumé,
  JSON, `.ics`) sont générés localement dans votre navigateur.
- L'historique des statuts est stocké **localement** dans le `localStorage` de votre
  navigateur (clé `anfExtensionStatusHistory:<idDossier>`). Vous pouvez l'effacer en
  vidant les données de site du portail — pensez à **Exporter JSON** avant si vous
  souhaitez le conserver.

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

1. Connectez-vous au portail ANEF : la frise de progression apparaît automatiquement
   sous l'en-tête du site.
2. Le panneau **Suivi & historique** se trouve juste en dessous. De haut en bas :
   l'alerte éventuelle liée à votre statut, les chips d'informations, la carte
   « Étape actuelle / étape suivante », les métriques de délais, puis l'historique
   de vos changements de statut.
3. Boutons du panneau :
   - **Copier le résumé** — récapitulatif texte dans le presse-papiers ;
   - **Exporter JSON** — télécharge l'historique et les infos du dossier ;
   - **Entretien → calendrier** — (si un entretien à venir est détecté) télécharge
     un fichier `.ics` avec rappel la veille ;
   - **Masquer / Afficher** — replie ou déplie le panneau.
4. L'historique se construit automatiquement : chaque visite où un nouveau statut est
   détecté ajoute une entrée. Visitez le portail régulièrement pour ne rien manquer.
5. Pour le diagnostic, ouvrez la console développeur (`F12`) et tapez `__ANF_API_INFOS__`
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
(`extensionVersion`) à chaque release, et à documenter les changements dans
[`CHANGELOG.md`](CHANGELOG.md).
