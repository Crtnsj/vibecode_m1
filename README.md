# ⏳ TimeTravel Agency — Webapp Interactive

> Webapp pour une agence de voyage temporel fictive de luxe, créée avec IA générative.

🌐 **Webapp déployée** : [https://crtnsj.github.io/vibecode_m1/](https://crtnsj.github.io/vibecode_m1/)
📦 **Repository GitHub** : [https://github.com/Crtnsj/vibecode_m1](https://github.com/Crtnsj/vibecode_m1)

---

## 🛠️ Stack Technique

| Technologie                       | Usage                                                       |
| --------------------------------- | ----------------------------------------------------------- |
| HTML5 / CSS3 / JavaScript ES6+    | Application single-page, zéro framework                     |
| CSS Custom Properties (variables) | Thème cohérent dark mode luxe                               |
| CSS Keyframes & Transitions       | Animations (particules, reveal, shimmer)                    |
| IntersectionObserver API          | Animations déclenchées au scroll                            |
| Google Fonts                      | Typographies : Playfair Display, Cormorant Garamond, Outfit |
| Mistral AI API                    | Chatbot conversationnel intelligent                         |
| GitHub Pages                      | Hébergement & déploiement                                   |

---

## ✨ Features Implémentées

### Phase 1 — Architecture & Design

- Navigation fixe avec effet glassmorphism au scroll (backdrop-filter)
- Hero section immersive : particules animées JS, titre doré avec animation shimmer, badge animé
- Section "À propos" avec grille responsive et statistiques clés
- Indicateur de scroll animé

### Phase 2 — Galerie des Destinations

- 3 cards interactives avec hover effects (scale image, border dorée, shadow)
- Modal détaillé par destination : description, tarifs, durée, difficulté, points forts
- Animations au scroll via IntersectionObserver (fade-up avec delays décalés)
- Images Unsplash en placeholder (remplaçables par les visuels du Projet 1)

### Phase 3 — Intelligence Artificielle

#### 🤖 Chatbot "Chronos" — Mistral AI

- **Modèle** : `mistral-small-latest` via l'API REST Mistral AI
- **System prompt** personnalisé avec la personnalité de Chronos (guide temporel professionnel et chaleureux)
- **Mémoire conversationnelle** : historique des 20 derniers messages conservé pour le contexte
- **Widget flottant** en bas à droite avec :
  - Bulle de chat avec indicateur "En ligne"
  - Indicateur de frappe (typing dots) pendant le chargement
  - Suggestions de questions cliquables
  - Support du formatage (gras, retours à la ligne)
  - Gestion d'erreurs avec message de fallback
- **Connaissances injectées** : tarifs, durées, activités, sécurité pour les 3 destinations

#### 🎯 Quiz de Personnalisation

- 4 questions interactives avec barre de progression visuelle
- Algorithme de scoring : chaque réponse attribue un point à une destination
- Résultat personnalisé avec emoji, titre et description adaptée
- Possibilité de recommencer

### Phase 4 — Déploiement

- Fichier HTML unique (zero build step)
- Déployé sur GitHub Pages
- Compatible mobile, tablette et desktop

---

## 📐 Architecture Technique

### Structure du fichier unique

```
index.html
├── <head>
│   ├── Meta tags & viewport responsive
│   ├── Google Fonts (Playfair Display, Cormorant Garamond, Outfit)
│   └── <style> — CSS complet (~700 lignes)
│       ├── Variables CSS (:root) — couleurs, fonts, easings
│       ├── Reset & scrollbar custom
│       ├── Grain overlay (SVG noise texture)
│       ├── Animations (@keyframes) — fadeUp, shimmer, float, pulse-ring
│       ├── Navigation (fixe, glassmorphism, responsive)
│       ├── Hero section (particules, badge, titre, CTA)
│       ├── Sections communes (headers, dividers)
│       ├── About (grille, stats)
│       ├── Destinations (cards, hover, modals)
│       ├── Quiz (progress bar, options, résultats)
│       ├── Chatbot (widget, messages, typing, suggestions)
│       ├── Footer
│       └── Media queries (1024px, 768px)
├── <body>
│   ├── Navigation avec liens smooth scroll
│   ├── Hero avec particules générées en JS
│   ├── Section About avec statistiques
│   ├── Section Destinations — 3 cards cliquables
│   ├── Modal overlay pour détails destination
│   ├── Section Quiz — 4 questions interactives
│   ├── Footer
│   ├── Widget Chatbot (toggle + window)
│   └── <script> — JavaScript (~200 lignes)
│       ├── Génération de particules (30 éléments DOM)
│       ├── Navbar scroll effect (scroll listener)
│       ├── IntersectionObserver pour animations reveal
│       ├── Système de modals (open/close avec données dynamiques)
│       ├── Quiz engine (scoring, progression, résultats)
│       ├── Chatbot Mistral AI (fetch API, historique, system prompt)
│       └── Smooth scroll navigation
```

### Appel API Mistral AI — Détails techniques

```
Endpoint : POST https://api.mistral.ai/v1/chat/completions
Modèle   : mistral-small-latest
Headers  : Authorization: Bearer <API_KEY>, Content-Type: application/json

Payload :
{
  "model": "mistral-small-latest",
  "messages": [
    { "role": "system", "content": "<system prompt Chronos>" },
    { "role": "user", "content": "..." },
    { "role": "assistant", "content": "..." }
  ],
  "max_tokens": 500,
  "temperature": 0.7
}
```

- L'historique de conversation est maintenu côté client (array JS)
- Limité aux 20 derniers messages + system prompt pour éviter le dépassement de contexte
- Les réponses sont parsées pour supporter le gras (`**text**`) et les retours à la ligne

### Design System

| Variable CSS     | Valeur                                 | Usage                       |
| ---------------- | -------------------------------------- | --------------------------- |
| `--gold`         | `#c9a84c`                              | Couleur d'accent principale |
| `--bg-primary`   | `#0a0a0f`                              | Fond principal              |
| `--bg-card`      | `#16161f`                              | Fond des cards              |
| `--font-display` | Playfair Display                       | Titres                      |
| `--font-body`    | Outfit                                 | Corps de texte              |
| `--font-elegant` | Cormorant Garamond                     | Sous-titres, citations      |
| `--ease-smooth`  | `cubic-bezier(0.25, 0.46, 0.45, 0.94)` | Transitions fluides         |

---

## 🤖 Outils IA Utilisés (Transparence)

| Outil                  | Rôle               | Détail                                                                   |
| ---------------------- | ------------------ | ------------------------------------------------------------------------ |
| **Claude** (Anthropic) | Génération de code | Architecture complète HTML/CSS/JS, intégration API                       |
| **Mistral AI API**     | Chatbot "Chronos"  | Modèle `mistral-small-latest`, réponses conversationnelles en temps réel |
| **Unsplash**           | Images placeholder | À remplacer par les visuels du Projet 1 (Midjourney, DALL-E, Runway…)    |

---

## 📁 Structure du Repository

```
vibecode_m1/
├── index.html    — Application complète (HTML + CSS + JS)
└── README.md     — Documentation technique
```

---

## 🚀 Déploiement

Le site est déployé via **GitHub Pages** depuis la branche `main` du repository.

**URL publique** : [https://crtnsj.github.io/vibecode_m1/](https://crtnsj.github.io/vibecode_m1/)

### Reproduire le déploiement

1. Cloner le repo : `git clone https://github.com/Crtnsj/vibecode_m1.git`
2. Aller dans Settings → Pages → Source : Deploy from branch `main` / `/ (root)`
3. Le site est accessible en quelques minutes à `https://<username>.github.io/vibecode_m1/`

Aucune étape de build nécessaire — le fichier HTML est servi directement.

---

## 👥 Équipe

- Corentin SANJUAN

## 📄 Licence

Projet pédagogique — M1/M2 Digital & IA
