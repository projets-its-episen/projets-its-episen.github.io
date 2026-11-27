# Projets ITS

Vitrine des projets étudiants (MESPI et PoC) de la spécialité ITS (Ingénierie et Technologies pour la Santé) de l'EPISEN, avec ses deux parcours :
- **IA&D-S** : Intelligence Artificielle et Données de Santé
- **Cyber-S** : Cybersécurité en Santé

Initiative étudiante, site non officiel. En ligne sur **https://projets-its-episen.github.io**

Le site est un seul fichier, `index.html`, sans dépendance à installer. Les projets viennent d'un **formulaire Google** relié à un **tableau Google Sheets publié en CSV** : personne n'a besoin de toucher au code pour ajouter un projet.

---

## Au quotidien

- **Ajouter un projet** : n'importe qui clique sur « Ajouter mon projet » sur le site. Le projet apparaît quelques minutes après l'envoi, le temps que Google mette à jour la feuille publiée.
- **Retirer ou corriger un projet** : supprime ou modifie sa ligne dans le tableau Google Sheets. Il n'y a rien à faire sur le site.
- **Image d'un projet** : un lien Google Drive fonctionne s'il est partagé en « Tous les utilisateurs disposant du lien ». Sans image, le site génère une couverture unique pour le projet.
- **Vidéo** : un lien YouTube dans la question « Lien vidéo, poster ou GitHub » affiche un lecteur directement dans la fiche du projet.
- **Liens à partager** :
  - le site : `https://projets-its-episen.github.io`
  - le formulaire directement : `https://projets-its-episen.github.io/#ajouter`
  - un projet précis : bouton « Partager » dans sa fiche.

## Projets exemples

En attendant les vrais projets de la promo, le site affiche 21 **sujets exemples** (IA&D-S et Cyber-S) :
- marqués « Exemple » sur la carte et « Projet exemple (fictif) » dans la fiche ;
- **sans aucun nom d'étudiant** ;
- non comptés dans les statistiques.

Ils disparaissent automatiquement dès qu'il y a **8 vrais projets** (réglage `MASQUER_EXEMPLES_A_PARTIR_DE` dans le bloc `config`, mettre `0` pour ne jamais les afficher). Pour en modifier ou en retirer un, édite le bloc `exemples` en haut de `index.html`.

## Liste collaborative des entreprises (page Entreprises)

La page **#entreprises** affiche une liste d'entreprises remplie par les étudiants. Pour l'activer :

1. Crée un **nouveau formulaire Google** « Ajouter une entreprise ITS » avec ces questions (garde les mots en gras) :
   - **Nom de l'entreprise** (réponse courte, obligatoire)
   - **Secteur** d'activité (réponse courte)
   - **Ville** / pays (réponse courte)
   - Type d'**accueil** (cases à cocher : Stage 1re année, Stage 2e année (étranger), Stage 3e année, Alternance)
   - **Site** web (réponse courte)
   - **Commentaire** (paragraphe, facultatif)
2. Relie-le à un tableau Google Sheets, publie l'onglet des réponses en **CSV** (comme pour les projets).
3. Envoie les deux liens : ils vont dans `ENTREPRISES_CSV_URL` et `ENTREPRISES_FORM_URL` du bloc `config`.

Le bouton « Ajouter une entreprise » n'apparaît qu'une fois le formulaire relié. La colonne `Publié` fonctionne aussi ici pour valider avant affichage.

## Page Contacts

La page **https://projets-its-episen.github.io/#contacts** présente une carte par année (1re, 2e, 3e année).

- Par défaut, chaque carte affiche « Contact de promo à venir » et un bouton qui écrit à `CONTACT_EMAIL` avec l'année en objet (par exemple `[ING2] Question pour la promo`).
- Pour afficher un vrai contact, remplis le bloc `contacts` en haut de `index.html` (`nom`, `role`, `email`, `linkedin`). **Uniquement avec l'accord de la personne.**
- Le bouton « Proposer un stage ou un projet » envoie un e-mail à `CONTACT_EMAIL`. Les questions officielles (admissions, scolarité) renvoient vers le site de l'EPISEN.

## Modération (recommandé)

Par défaut, tout projet envoyé s'affiche automatiquement. Pour **valider les projets avant publication** :

1. Dans le tableau des réponses, ajoute une colonne à droite intitulée **`Publié`**.
2. Écris **`oui`** dans cette colonne pour chaque projet à afficher.

Dès que cette colonne existe, seuls les projets marqués `oui` apparaissent sur le site, et le formulaire prévient que le projet sera visible après vérification. Supprime la colonne pour revenir à la publication automatique.

Le lien « Signaler un contenu » en bas de page envoie un e-mail à l'adresse `CONTACT_EMAIL`.

## Configuration

Tout en haut de `index.html`, dans le bloc `config` :

```json
{
  "SHEET_CSV_URL": "lien CSV du tableau (Fichier > Partager > Publier sur le Web > CSV)",
  "FORM_URL": "lien du formulaire (bouton Envoyer > icône lien)",
  "CONTACT_EMAIL": "adresse qui reçoit les signalements"
}
```

Garde les guillemets et les virgules. Les projets de départ, toujours affichés, sont dans le bloc `seed`, juste en dessous.

## Questions du formulaire

Le site reconnaît les colonnes grâce aux mots en gras. Si tu renommes une question, garde ce mot.

| # | Titre de la question | Type | Obligatoire |
|---|---|---|---|
| 1 | **Nom du projet** | Réponse courte | Oui |
| 2 | **Type** de projet | Choix multiples : MESPI / PoC / Autre | Oui |
| 3 | **Année** / promo (ex. 2025-2026) | Réponse courte | Oui |
| 4 | **Domaine** | Choix multiples : IA & Data / Cybersécurité / IoT & capteurs / Réseaux / Imagerie / E-santé / Autre | Oui |
| 5 | **Résumé** en une phrase | Réponse courte | Oui |
| 6 | **Description** du projet (problème, solution) | Paragraphe | Non |
| 7 | **Technologies** utilisées (séparées par des virgules) | Réponse courte | Non |
| 8 | **Membres** de l'équipe (séparés par des virgules) | Réponse courte | Non |
| 9 | Lien d'une **image** (optionnel) | Réponse courte | Non |
| 10 | **Lien** vidéo, poster ou GitHub (optionnel) | Réponse courte | Non |
| 11 | **Parcours** | Choix multiples : IA&D-S (Intelligence Artificielle et Données de Santé) / Cyber-S (Cybersécurité en Santé) / Les deux | Recommandé |

**Parcours :** la question 11 permet d'afficher le badge IA&D-S ou Cyber-S sur chaque projet et de filtrer par parcours. Si elle est absente ou vide, le site devine le parcours à partir du domaine (IA, données, imagerie → IA&D-S ; cybersécurité → Cyber-S).

**Important :** le tableau publié est lisible par tout le monde. Ne collecte **pas** les adresses e-mail dans le formulaire (Paramètres → Réponses → « Collecter les adresses e-mail » désactivé), sinon elles seraient publiques.

## Sécurité

- Tout le contenu venant du formulaire est affiché comme du texte : un code envoyé dans une réponse n'est jamais exécuté.
- Seuls les liens `http(s)` sont acceptés. Les liens s'ouvrent dans un nouvel onglet, isolés du site.
- Une politique de sécurité (CSP) limite le site à Google (tableau, formulaire, polices) et YouTube (vidéos).
- Le script de la page est identifié par son empreinte `sha256` dans la CSP. **Si tu modifies le bloc `<script>` du bas de page, recalcule cette empreinte**, sinon le site ne s'affichera plus. Modifier le texte, `config` ou `seed` ne pose aucun problème.

## Fichiers

- `index.html` : le site complet.
- `og-image.jpg` : l'image d'aperçu affichée quand on partage le lien (LinkedIn, WhatsApp…).
- `robots.txt` et `sitemap.xml` : aident Google à référencer le site.

## Mise en ligne

Le site est publié automatiquement par GitHub Pages depuis la branche `main` (dossier racine). Toute modification enregistrée sur `main` est en ligne en 1 à 2 minutes.

## Passation

- Partage le **formulaire** et le **tableau** en tant qu'**éditeur** avec la personne qui reprend (BDE, enseignant, élève d'une autre promo).
- Sur GitHub, ajoute cette personne comme propriétaire de l'organisation `projets-its-episen` (**People → Invite member → Owner**).
