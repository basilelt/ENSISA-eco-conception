---
marp: true
theme: gaia
markdown.marp.enableHtml: true
paginate: true

<style>
    section {
    background-color: #fefefe;
    color: #333;
    font-size: 0.9em;
    }

    img[alt~="center"] {
    display: block;
    margin: 0 auto;
    }
    blockquote {
    background: #ffedcc;
    border-left: 10px solid #d1bf9d;
    margin: 1.5em 10px;
    padding: 0.5em 10px;
    }
    blockquote:before{
    content: unset;
    }
    blockquote:after{
    content: unset;
    }
    table { font-size: 0.78em; }
</style>

---

# TD 01 - Audit Éco-Conception : TikTok

Basile LE THIEC · Lilian NOACCO · Dorian POELLEN · Léon SCHER

Groupe 6 — ENSISA, 25 mars 2026

---

# Présentation du site analysé

**TikTok** (`tiktok.com`) — réseau social de courtes vidéos verticales, piloté par un algorithme de recommandation.

**Pages analysées :**
- 🏠 **Page d'accueil** — `tiktok.com/` — feed principal avec vidéos en autoplay
- 🔍 **Page Explore** — `tiktok.com/explore` — grille de découverte de contenus tendance

**Outils utilisés :**
| Outil | Homepage | Explore |
|---|---|---|
| Google Lighthouse | Perf **61** · A11y 74 · BP 73 | Perf **36** · A11y **92** · BP 54 |
| EcoIndex (calcul) | **9.6/100 → Grade G** | **24.9/100 → Grade F** |
| Green Web Foundation | ❌ TikTok **n'utilise pas** d'énergie verte | — |
| Référentiels | RGESN, Opquast | — |

---

# 5 points les plus problématiques

1. **Poids de page et nombre de requêtes excessifs**
   _Homepage : 10 Mo, 391 requêtes · Explore : 5 Mo, 185 requêtes_

2. **JavaScript massif et non utilisé (obésiciel)**
   _1,8 Mo de JS inutile (homepage) · TTI : 8,6 s (home), 21,6 s (explore)_

3. **Algorithme de recommandation & autoplay infini (dark pattern)**
   _Design conçu pour maximiser le temps d'écran, pas l'utilité_

4. **Hébergement non vert + empreinte carbone élevée**
   _EcoIndex G (homepage) : 2,81 gCO2e, 4,21 cl d'eau par visite_

5. **Accessibilité et impacts sociaux insuffisants**
   _A11y 74/100 sur la homepage ; cyberharcèlement, santé mentale, modération IA opaque_

---

# Pourquoi ces points posent problème

| # | Problème | Impact éco-conception |
|---|---|---|
| 1 | 10 Mo / 391 requêtes | Consommation réseau élevée, incompatible avec terminaux anciens → **obsolescence forcée** |
| 2 | 1,8 Mo JS inutilisé | **Obésiciel** : surcharge CPU 6,1 s, consomme batterie, force l'achat de matériel neuf |
| 3 | Autoplay & scroll infini | **Effet rebond** : chaque optimisation UX augmente le temps passé → +data, +énergie |
| 4 | Hébergement non vert | EcoIndex **G** = pire percentile ; ~2,81 gCO2e × milliards de visites/jour |
| 5 | Accessibilité 74/100 | **Exclusion numérique** (ODD 10) ; cyberharcèlement = impact social négatif majeur |

> L'éco-conception englobe les 3 piliers du développement durable : environnement, économie, **social**.

---

# Améliorations proposées

| # | Action concrète | Acteur(s) |
|---|---|---|
| 1 | Lazy-loading des médias, compression Brotli, CDN intelligent, mise en cache agressive | Dev backend, DevOps |
| 2 | Tree-shaking, code splitting, audits Lighthouse en CI/CD, réduire les dépendances | Dev frontend, Tech Lead |
| 3 | Limiter l'autoplay par défaut, proposer un "mode sobre" avec pause auto, supprimer le scroll infini | Designer, Product Owner |
| 4 | Migrer l'hébergement vers des fournisseurs certifiés énergie verte (label Green Web Foundation) | DevOps, Manager |
| 5 | Audits RGAA/axe réguliers, alt-texts systématiques, renforcer la modération humaine, transparence algo | Dev, Designer, Trust & Safety |

---

# Conclusion

**Ce que nous avons appris :**

- L'éco-conception dépasse la performance technique : elle couvre l'**accessibilité**, l'**éthique** et les **effets rebond**
- TikTok illustre le paradoxe : service très fluide en apparence, mais **Grade G EcoIndex** (pire classe)
- Les **dark patterns** (autoplay, scroll infini) sont un problème d'éco-conception à part entière
- Le fait que TikTok **n'utilise pas d'énergie verte** démultiplie son impact à l'échelle mondiale
- Les outils (Lighthouse, EcoIndex) permettent de **quantifier** des problèmes qui semblent abstraits

**Comment nous l'avons vécu :**
Exercice révélateur — difficile de mesurer en temps réel (outils limités), mais les données Lighthouse suffisent à objectiver l'empreinte d'un géant numérique.
