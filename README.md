# Projets ITS : mise en ligne (environ 20 minutes, une seule fois)

Le site est un seul fichier, `index.html`. Les projets ajoutés passent par un **formulaire Google** : chaque réponse s'affiche automatiquement sur le site, sans toucher au code.

---

## Étape 1 : créer le formulaire Google

Va sur forms.google.com, puis crée un formulaire vide intitulé « Ajouter mon projet ITS ».

Ajoute **ces questions, avec ces titres** (le site reconnaît les colonnes grâce aux mots en gras) :

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

Dans les paramètres du formulaire, **désactive** l'option « Limiter à 1 réponse » et la connexion obligatoire, pour que tout le monde puisse répondre sans compte Google.

## Étape 2 : relier le formulaire à un tableau Google Sheets

1. Dans l'onglet **Réponses**, clique sur **Associer à Sheets**, puis choisis de créer une feuille de calcul.
2. Dans cette feuille, va dans **Fichier → Partager → Publier sur le Web**.
3. Choisis l'onglet des réponses, le format **Valeurs séparées par des virgules (.csv)**, puis clique sur **Publier**.
4. **Copie le lien** obtenu.

## Étape 3 : coller les 2 liens dans `index.html`

Ouvre `index.html` avec le Bloc-notes. Tout en haut du fichier, remplis :

```js
const CONFIG = {
  SHEET_CSV_URL: "colle ici le lien CSV de l'étape 2",
  FORM_URL: "colle ici le lien du formulaire",
};
```

Pour trouver le lien du formulaire : bouton **Envoyer**, puis l'icône 🔗, puis copier.

## Étape 4 : mettre le site en ligne avec GitHub Pages (gratuit)

1. Connecte-toi à github.com avec le compte **`projets-its-episen`**, puis clique sur **New repository**.
2. Nomme-le exactement `projets-its-episen.github.io`, en **Public**.
3. Clique sur **Add file → Upload files**, glisse `index.html`, puis clique sur **Commit changes**.
4. Va dans **Settings → Pages** : Source « Deploy from a branch », Branch `main`, dossier `/ (root)`, puis **Save**.
5. Au bout de 1 à 2 minutes, le site est en ligne à l'adresse **https://projets-its-episen.github.io**

C'est ce lien que tu partages : LinkedIn de l'école, Mellouk, groupe de promo.

---

## Au quotidien

- **Ajouter un projet** : n'importe qui clique sur « Ajouter mon projet » sur le site. Le projet apparaît quelques minutes après l'envoi, le temps que Google mette à jour la feuille publiée.
- **Retirer ou corriger un projet** : supprime ou modifie la ligne dans le tableau Google Sheets. Il n'y a rien à faire sur le site.
- **Image d'un projet** : un lien Google Drive fonctionne s'il est partagé en « Tous les utilisateurs disposant du lien ». Sans image, le site génère automatiquement une couverture colorée.

## Passation (quand tu ne veux plus t'en occuper)

- Partage le **formulaire** et le **tableau** en tant qu'**éditeur** avec la personne qui reprend (BDE, enseignant, élève d'une autre promo).
- Sur GitHub, va dans **Settings → Collaborators** pour ajouter cette personne, ou dans **Settings → Transfer** pour lui donner le dépôt.
