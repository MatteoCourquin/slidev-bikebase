---
background: https://images.unsplash.com/photo-1568772585407-9361f9bf3a87?auto=format&fit=crop&q=80&w=2670&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
class: text-center
lineNumbers: false
transition: slide-left
title: Bike Base • Library
mdc: true
fonts:
  sans: 'Helvetica Neue,Robot'
  local: 'Helvetica Neue'

---

# Bike Base

Cette librairie contient un ensemble de fonctions JavaScript permettant de gérer un catalogue de motos. Voici un aperçu des différentes fonctionnalités disponibles.

<div class="abs-br m-6 flex gap-2">
  <a href="https://github.com/LouisPerre/BikeBase" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---
transition: fade-out
---

## Besoins et Origines • Pourquoi cette Bibliothèque?

<br>
<hr>
<br>

- **L'Insuffisance des Données**

Les développeurs avaient besoin d'un accès facile à des données complètes et précises sur les motos pour divers projets.

- **La Complexité du Tri et du Filtrage**

Filtrer les motos par marque, puissance, année, et conformité à la norme A2 était un défi, nécessitant un outil puissant et flexible.

- **La Nécessité de la Personnalisation**

Les projets variaient, nécessitant des données personnalisées triées et filtrées selon des critères spécifiques.

---
transition: fade-out
---

## Problématique Résolue • La Solution Proposée

<br>
<hr>
<br>

- Données Complètes et Structurées

La bibliothèque fournit un accès facile à une vaste base de données de motos, complètement organisée et structurée.

- Filtrage Puissant et Flexible

Les développeurs peuvent filtrer les motos par marque, puissance, année et conformité à la norme A2 grâce à des fonctions simples et flexibles.

- Personnalisation Selon les Besoins

La bibliothèque offre des fonctions permettant aux développeurs de personnaliser les données selon leurs besoins spécifiques pour différents projets.

---
transition: fade-out
---

## Bibliothèque • bikebase

<br>
<hr>
<br>

- Description:

*bikebase est une bibliothèque JavaScript puissante et conviviale qui offre un accès simplifié à une vaste base de données de motos. Cette bibliothèque est conçue pour les développeurs web et les passionnés de motos, offrant des fonctionnalités avancées de filtrage et de personnalisation des données.*

- Lien npm:

[![Github](https://img.shields.io/github/v/release/LouisPerre/BikeBase)](https://github.com/LouisPerre/BikeBase)
<br>
[![NPM](https://img.shields.io/npm/v/bikebase.svg)](https://www.npmjs.com/package/bikebase)
<br>
[![NPM](https://img.shields.io/npm/dm/wealtify.svg)](https://www.npmjs.com/package/bikebase)

---
transition: fade-out
---

## Code • Aperçu du Code Source

<br>
<hr>
<br>

```javascript
  getAllBikes: () => bikes,
```
```javascript
  getAllBikesA2: () => {
    const bikesWithA2 = _.mapValues(bikes, (brandBikes) =>
      _.filter(brandBikes, { a2: true })
    );
    return _.pickBy(bikesWithA2, (brandBikes) => brandBikes.length > 0);
  },
```
```javascript
  getBikesByBrand: (brand) => {
    const err = 'brand must be a string';
    if (typeof brand !== 'string') return { err };
    return bikes[brand];
  },
```
```javascript
  getBikesByPower: (power_hp, tolerance = 0) => _.chain(bikes).flatMap((bikes) => bikes).filter((bike) => _.inRange(bike.power_hp, power_hp - tolerance, power_hp + tolerance + 1)).value()
```
```javascript
  getBikesByYear: (year) => _.chain(bikes).map((bikeList) => bikeList).flatten().filter((bike) => bike.year_launched < year).value()
```

---
transition: fade-out
---

## Installation

<br>
<hr>
<br>

- Installation via npm:

```bash
npm install bikebase
```

- Import into your project:

```javascript
const bikebase = require('bikebase');
```

- Using the functions:

```javascript
// Examples of using the library's functions
const allBikes = bikebase.getAllBikes();
const a2Bikes = bikebase.getAllBikesA2();
const yamahaBikes = bikebase.getBikesByBrand('yamaha');
const powerfulBikes = bikebase.getBikesByPower(100, 10);
const vintageBikes = bikebase.getBikesByYear(1990);
```

---
transition: fade-out
---

## Documentation

<br>
<hr>
<br>

La méthode `getAllBikes()` renvoie un tableau contenant toutes les motos de la base de données.

La méthode `getAllBikesA2()` renvoie un objet contenant des motos adaptées aux détenteurs du permis A2.

La méthode `getBikesByBrand(brand)` prend en paramètre le nom d'une marque de moto et renvoie un tableau contenant les modèles de cette marque.

La méthode `getBikesByPower(power_hp, tolerance)` prend en paramètre une puissance en chevaux et une tolérance, et renvoie les motos dont la puissance est proche de la valeur spécifiée.

La méthode `getBikesByYear(year)` prend en paramètre une année de lancement et renvoie les motos lancées avant cette année.

---
transition: fade-out
---

## Tests

<br>
<hr>
<br>

La bibliothèque bikebase est rigoureusement testée pour garantir son bon fonctionnement. Voici un aperçu de la couverture des tests unitaires : 

La méthode `getAllBikes()` est testée pour s'assurer qu'elle renvoie toutes les motos de la base de données. 

La méthode `getAllBikesA2()` est testée pour vérifier qu'elle renvoie uniquement les motos adaptées aux détenteurs du permis A2. 

La méthode `getBikesByBrand(brand)` est testée avec différents noms de marques pour garantir qu'elle renvoie les modèles appropriés. 

La méthode `getBikesByPower(power_hp, tolerance)` est testée avec différentes valeurs de puissance et de tolérance pour s'assurer qu'elle renvoie les motos correctes en fonction des critères spécifiés. 


La couverture complète des tests unitaires assure la fiabilité de chaque fonctionnalité de la bibliothèque.

---
transition: fade-out
---

## Roadmap

<br>
<hr>
<br>

La bibliothèque bikebase est en constante évolution, et voici un aperçu des fonctionnalités et améliorations prévues pour les prochaines versions :

- Version 1.1.0 (À venir)

**Fonction de recherche avancée :** Ajout d'une fonction de recherche avancée permettant aux utilisateurs de filtrer les motos par plusieurs critères, tels que la puissance, l'année de lancement et le type de moto.

**Optimisation des performances :** Optimisation des requêtes et des algorithmes pour améliorer la vitesse et l'efficacité de la bibliothèque, garantissant ainsi une expérience utilisateur plus fluide.

**Support multilingue :** Ajout de la prise en charge de plusieurs langues pour les messages d'erreur et les retours utilisateur, rendant la bibliothèque plus accessible à un public international.

---
transition: fade-out
---

## Roadmap

<br>
<hr>
<br>

- Version 1.2.0 (À venir)

**Intégration de données en temps réel :** Intégration de flux de données en temps réel pour que la bibliothèque puisse mettre à jour les informations sur les motos à mesure qu'elles deviennent disponibles.

**Filtrage avancé :** Ajout de fonctionnalités de filtrage avancées, y compris la capacité de trier les résultats par différents critères tels que la popularité, le prix et les évaluations des utilisateurs.

**Compatibilité avec d'autres plateformes :** Développement de versions de la bibliothèque compatibles avec d'autres plateformes, y compris les applications mobiles iOS et Android, pour offrir une expérience utilisateur cohérente sur toutes les plateformes.

Cette roadmap est sujette à modifications et sera mise à jour régulièrement en fonction des retours de la communauté et des besoins des utilisateurs.
