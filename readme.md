# IIBS Events

Site vitrine des événements de l'IIBS Dakar — projet de fin de semestre (L1/S2, Développement Web et Mobile).

Le site présente les événements du campus (conférences, ateliers, compétitions, forums, journées portes ouvertes, vie de campus), permet de consulter le détail de chaque événement, de s'inscrire, de découvrir les actualités et la galerie photo, et de contacter l'école.

---

## Aperçu


| **École** | IIBS Dakar |
| **Filière** | Web et Mobile Development — L1/S2 |
| **Maquette Figma** | [Lien Figma](https://www.figma.com/design/bnRopcTdAViMHQaANVSGuC/IIBS-EVENTS---FIGMA?node-id=1-216&t=Kx9jCyjaLQXKsxU9-1) |
| **Démo en ligne (GitHub Pages)** | https://github.com/Ndiaye-Fallou/Projet-Examen-L1-S2-Coach-DIOUF |

---

## Stack technique

- **HTML5** sémantique
- **Tailwind CSS** via CDN (`cdn.tailwindcss.com`) — aucun outil de build (npm/PostCSS) requis
- **Polices** : Poppins (titres) et Inter (texte courant), via Google Fonts

---

## Structure du projet

```
iibs-events/
├── index.html                 # Accueil
├── agenda.html                 # Agenda des évènements
├── detail-hackathon.html       # Détail d'un évènement (exemple : Hackaton IIBS 2026)
├── actualites.html             # Actualités et galerie photo
├── contact.html                # Contact et accès (page bonus)
├── inscription.html            # Formulaire d'inscription
├── assets/
│   └── images/
│       ├── hero.jpg
│       ├── chart.jpg
│       ├── events/             # Visuels des cartes évènements
│       ├── detail/              # Visuels des pages détail
│       ├── actualites/          # Visuels des articles
│       ├── gallery/             # Photos de la galerie
│       ├── contact/             # Visuels de la page Contact
│       ├── avatars/             # Avatars des intervenants
│       └── README.txt           # Liste des fichiers images attendus
└── README.md
```

> **Remarque sur la page Détail** : par souci de simplicité (pas de backend, pas de JS de routage), chaque évènement a sa propre page HTML statique, sur le modèle de `detail-hackathon.html`. Les 5 autres pages détail (`detail-portes-ouvertes.html`, `detail-forum.html`, `detail-conference-ia.html`, `detail-git-github.html`, `detail-demo-day.html`) suivent exactement la même structure avec un contenu différent.

---

## Pages du site

| Page | Fichier | Description |
|---|---|---|
| Accueil | `index.html` | Hero, évènement à la une, prochains rendez-vous, chiffres clés |
| Agenda | `agenda.html` | Liste filtrable des 6 évènements |
| Détail évènement | `detail-*.html` | Description complète, programme, intervenants, infos pratiques |
| Actualités et galerie | `actualites.html` | Articles récents + galerie photo |
| Inscription | `inscription.html` | Formulaire d'inscription à un évènement |
| Contact | `contact.html` | Coordonnées, carte interactive (page bonus) |

---

## Design system

- **Couleurs principales**
  - Fond sombre (header, footer, cartes) : bleu marine `#0a0e23` → `#121a3f`
  - Accent : vert `#22c55e` (boutons d'action, badges de catégorie)
  - Titres du footer : or `#e3c567`
- **Typographies** : Poppins (600–800) pour les titres, Inter (400–600) pour le texte courant
- **Composants réutilisables** : carte évènement, badge de catégorie, bouton primaire/secondaire, champ de formulaire — dupliqués manuellement dans chaque page HTML (pas de système d'inclusion, cf. limitations)

---

## Responsive et accessibilité

- Points de rupture Tailwind utilisés : mobile par défaut, `sm:`, `md:`, `lg:`
- **Menu burger 100 % CSS, sans JavaScript** : technique du *checkbox hack* (case à cocher invisible + `<label for="">` + classes `peer` / `peer-checked:`) pour afficher/masquer le menu mobile
- Textes alternatifs (`alt`) sur toutes les images informatives
- États de focus clavier visibles (`focus-visible`) sur les liens, boutons et champs
- Contraste texte/fond vérifié sur les zones sombres et claires
- Structure sémantique : `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`

---

## Limitations et choix assumés

Le projet respecte la contrainte « HTML + Tailwind CSS, sans JavaScript », à deux exceptions près, assumées et documentées :

1. **Confirmation d'inscription** (`inscription.html`) : un script de quelques lignes intercepte l'envoi du formulaire (`preventDefault`) et affiche un message « Inscription confirmée » à la place du formulaire. Sans backend, il n'y a pas d'envoi réel des données ni d'e-mail envoyé.
2. **Carte de localisation** (`contact.html`) : la carte est une intégration Google Maps (`<iframe>`). Le code écrit par l'équipe ne contient pas de JavaScript ; Google Maps utilise en interne son propre JS, hors de notre contrôle.

Autres limitations connues :
- Pas de backend : aucune donnée n'est réellement sauvegardée (inscriptions, formulaire de contact)
- Les filtres et la recherche de l'Agenda sont visuels (boutons stylés) mais non fonctionnels, en l'absence de JavaScript
- Chaque évènement a sa propre page HTML dupliquée plutôt qu'une page unique alimentée dynamiquement, ce qui entraîne une répétition de code assumée

---

## Lancer le projet en local

Aucune installation n'est nécessaire.

1. Cloner le dépôt :
   ```bash
   git clone https://github.com/<utilisateur>/iibs-events-<nom-du-groupe>.git
   cd iibs-events-<nom-du-groupe>
   ```
2. Ouvrir `index.html` directement dans un navigateur, **ou** lancer un petit serveur local (recommandé pour que les chemins d'images fonctionnent correctement) :
   ```bash
   # avec Python
   python3 -m http.server 8000
   # puis ouvrir http://localhost:8000
   ```

---

## Déploiement (GitHub Pages)

1. Pousser le projet sur un dépôt GitHub public nommé `iibs-events-<nom-du-groupe>`
2. Aller dans **Settings > Pages** du dépôt
3. Choisir la branche `main` (dossier `/root`) comme source
4. Le site est ensuite accessible à l'adresse :
   'https://ndiaye-fallou.github.io/Projet-Examen-L1-S2-Coach-DIOUF/index.html'
5. Mettre à jour le lien dans la section [Aperçu](#aperçu) une fois déployé

---

## Crédits

Projet réalisé dans le cadre du cours de Développement Web et Mobile — IIBS Dakar, 2026.
Maquette conçue sur Figma, intégration HTML/Tailwind CSS réalisée par l'équipe.