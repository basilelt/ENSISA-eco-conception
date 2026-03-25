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

Groupe 6

---

# Présentation du site analysé

**TikTok** — réseau social de courtes vidéos verticales, piloté par un algorithme de recommandation.

**Pages analysées :**
- **Page d'accueil** — `https://www.tiktok.com` — feed principal avec vidéos en autoplay
- **Page Explore** — `https://www.tiktok.com/explore` — grille de découverte de contenus tendance

![jaaaj](https://hackmd.io/_uploads/H19Nx_Wsbx.png)

---

**Outils utilisés :**
| Outil | Homepage | Explore |
|---|---|---|
| Google Lighthouse | Perf **61** · A11y (Accessibilité) **74** · BP (Best Practices) **73** | Perf **36** · A11y **92** · BP **54** |
| EcoIndex | **33/100 → Grade E** · 5,03 Mo · 228 requêtes · 509 DOM | **24.9/100 → Grade F** |
| Green Web Foundation | TikTok **n'utilise pas** d'énergie verte (pas référencé sur le site)| — |
| GreenIT | Score **D** sur une page de vidéo. Sur la page d'une vidéo, on a **41.60** comme "EcoIndex", **3.25cl** d'eau, et **2.17g** de GES (gCO2e) consommé.| Score **F** sur la page explore ; **13.28** comme score "EcoIndex", **4.10cl** d'eau, et **2.73g** de GES consommé.| 
| Carbonalyzer | Test de 1 minute : **117MB** - **17g** de CO2 - 2 recharges de téléphone | Test de 1 minute : **163MB** - **20g** de CO2 - 2 recharges de téléphone |
    
![Screenshot 2026-03-25 at 15.22.39](https://hackmd.io/_uploads/SJ861OWjWe.png)

---

# 5 points les plus problématiques

<div class="columns">
<div>

1. **Poids de page et nombre de requêtes excessifs** — Homepage : >10 Mo, 391 requêtes — Explore : 5 Mo, 185 requêtes
2. **JavaScript massif et non utilisé (obésiciel)** — 1,8 Mo de JS inutile (homepage) — TTI : 8,6 s (home), 21,6 s (explore)
3. **Algorithme de recommandation & autoplay infini (dark pattern)**
   Design conçu pour maximiser le temps d'écran, pas l'utilité
4. **Mauvaise sobriété environnementale confirmée par EcoIndex**
   Homepage : score **33/100 (grade E)** · 5,03 Mo · 228 requêtes · 509 éléments DOM
5. **Accessibilité et impacts sociaux insuffisants**
   A11y 74/100 ; cyberharcèlement, santé mentale, modération IA opaque

</div>
<div>

![EcoIndex score](https://hackmd.io/_uploads/SJOy6PbiZe.png)

</div>
</div>

---

# Pourquoi ces points posent problème

| # | Problème | Impact éco-conception |
|---|---|---|
| 1 | 10 Mo / 391 requêtes | Consommation réseau élevée, incompatible avec terminaux anciens → **obsolescence forcée** |
| 2 | 1,8 Mo JS inutilisé | **Obésiciel** : surcharge CPU 6,1 s, consomme batterie, force l'achat de matériel neuf |
| 3 | Autoplay & scroll infini | **Effet rebond** : chaque optimisation UX augmente le temps passé → +data, +énergie |
| 4 | Mauvaise note EcoIndex | La homepage obtient **33/100 (grade E)** : le problème vient surtout du **poids de page** et du **nombre élevé de requêtes**, plus que de la complexité DOM |
| 5 | Accessibilité 74/100 | **Exclusion numérique** ; cyberharcèlement = impact social négatif majeur |

---

# Améliorations proposées

| # | Action concrète | Acteur(s) |
|---|---|---|
| 1 | **Lazy-loading** des médias, compression, CDN, cache | Dev backend, DevOps |
| 2 | **Audits Lighthouse** en CI/CD, réduire les dépendances | Dev frontend, Tech Lead |
| 3 | **Limiter l'autoplay** par défaut, **"mode sobre"** avec pause auto, **supprimer le scroll infini** | Designer, Product Owner |
| 4 | **Réduire le poids initial de la page** et le nombre de requêtes, puis migrer vers un hébergement plus sobre/vert | DevOps, Dev frontend, Manager |
| 5 | **Audits**, alt-texts systématiques, renforcer la modération humaine, transparence algo | Dev, Designer, Safety Team |

---

# Conclusion

**Ce que nous avons appris :**

- L'éco-conception dépasse la performance technique : elle couvre l'**accessibilité**, l'**éthique** et les **effets rebond**
- TikTok illustre le paradoxe : service fluide en apparence, mais **note E sur EcoIndex** sur la homepage, à cause d'une page lourde et très bavarde en requêtes réseau
- Les **dark patterns** (autoplay, scroll infini) sont un problème d'éco-conception à part entière
- Le fait que TikTok **n'utilise pas d'énergie verte** démultiplie son impact à l'échelle mondiale
- Les outils (Lighthouse, EcoIndex) permettent de **quantifier** des problèmes qui semblent abstraits

**Comment nous l'avons vécu :**
Exercice révélateur — difficile de mesurer en temps réel (outils limités), mais les données Lighthouse suffisent à objectiver l'empreinte d'un géant numérique.
