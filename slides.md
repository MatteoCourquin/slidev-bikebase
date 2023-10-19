---
theme: geist
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

This repository contains a set of JavaScript functions to manage a motorcycle catalog. Here's an overview of the different functionalities available.

<div class="abs-br m-6 flex gap-2">
  <a href="https://github.com/LouisPerre/BikeBase" target="_blank" alt="GitHub" title="Open in GitHub"
    class="text-xl slidev-icon-btn opacity-50 !border-none !hover:text-white">
    <carbon-logo-github />
  </a>
</div>

---
transition: fade-out
---

## Besoins et Origines

### **Pourquoi cette Bibliothèque?**

#### - _L'Insuffisance des Données_

- Les développeurs avaient besoin d'un accès facile à des données complètes et précises sur les motos pour divers projets.

#### - _La Complexité du Tri et du Filtrage_

- Filtrer les motos par marque, puissance, année, et conformité à la norme A2 était un défi, nécessitant un outil puissant et flexible.

#### - _La Nécessité de la Personnalisation_

- Les projets variaient, nécessitant des données personnalisées triées et filtrées selon des critères spécifiques.

#### - _L'Inspiration à Créer une Solution_

- C'est dans ce contexte que la Motorcycle Catalog Library est née, pour résoudre ces problèmes et faciliter la vie des développeurs.

---
transition: fade-out
---

## Problématique Résolue

### **La Solution Proposée**

#### - _Données Complètes et Structurées_

- La bibliothèque fournit un accès facile à une vaste base de données de motos, complètement organisée et structurée.

#### - _Filtrage Puissant et Flexible_

- Les développeurs peuvent filtrer les motos par marque, puissance, année et conformité à la norme A2 grâce à des fonctions simples et flexibles.

#### - _Personnalisation Selon les Besoins_

- La bibliothèque offre des fonctions permettant aux développeurs de personnaliser les données selon leurs besoins spécifiques pour différents projets.

#### - _Optimisation du Workflow_

- La solution permet de gagner du temps et d'optimiser le processus de développement en fournissant des données précises et adaptées à chaque cas d'utilisation.

---
transition: fade-out
---

## Bibliothèque

### **Nom: MotoDB**

#### **Description:**

MotoDB est une bibliothèque JavaScript puissante et conviviale qui offre un accès simplifié à une vaste base de données de motos. Cette bibliothèque est conçue pour les développeurs web et les passionnés de motos, offrant des fonctionnalités avancées de filtrage et de personnalisation des données.

#### **Lien npm:**

[![Github](https://img.shields.io/github/v/release/LouisPerre/BikeBase)](https://github.com/LouisPerre/BikeBase)
[![NPM](https://img.shields.io/npm/v/bikebase.svg)](https://www.npmjs.com/package/bikebase)
[![NPM](https://img.shields.io/npm/dm/wealtify.svg)](https://www.npmjs.com/package/bikebase)

---
transition: fade-out
---

## Code

#### **Aperçu du Code Source:**

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

To install the MotoDB library, follow these simple steps:

###### Installation via npm:

```bash
npm install motodb
```

###### Import into your project:

```javascript
const motodb = require('motodb');
```

###### Using the functions:

```javascript
// Examples of using the library's functions
const allBikes = motodb.getAllBikes();
const a2Bikes = motodb.getAllBikesA2();
const yamahaBikes = motodb.getBikesByBrand('Yamaha');
const powerfulBikes = motodb.getBikesByPower(100, 10);
const vintageBikes = motodb.getBikesByYear(1990);
```

By following these steps, you can easily integrate MotoDB into your project and start using its features to access and manipulate motorcycle data.
---
transition: fade-out
---

## Documentation

La bibliothèque MotoDB offre des fonctionnalités puissantes pour rechercher et filtrer des données sur les motos. Voici un aperçu de ses principales méthodes :

### `getAllBikes()`

Cette méthode renvoie un tableau contenant toutes les motos de la base de données.

```javascript
const motodb = require('motodb');
const allBikes = motodb.getAllBikes();
console.log(allBikes);
```

### `getAllBikesA2()`

Cette méthode renvoie un objet contenant des motos adaptées aux détenteurs du permis A2.

```javascript
const motodb = require('motodb');
const a2Bikes = motodb.getAllBikesA2();
console.log(a2Bikes);
```

### `getBikesByBrand(brand)`

Cette méthode prend en paramètre le nom d'une marque de moto et renvoie un tableau contenant les modèles de cette marque.

```javascript
const motodb = require('motodb');
const yamahaBikes = motodb.getBikesByBrand('Yamaha');
console.log(yamahaBikes);
```

### `getBikesByPower(power_hp, tolerance)`

Cette méthode prend en paramètre une puissance en chevaux et une tolérance, et renvoie les motos dont la puissance est proche de la valeur spécifiée.

```javascript
const motodb = require('motodb');
const powerfulBikes = motodb.getBikesByPower(100, 10);
console.log(powerfulBikes);
```

### `getBikesByYear(year)`

Cette méthode prend en paramètre une année de lancement et renvoie les motos lancées avant cette année.

```javascript
const motodb = require('motodb');
const vintageBikes = motodb.getBikesByYear(1990);
console.log(vintageBikes);
```

Pour plus de détails sur chaque méthode et ses options, veuillez consulter la documentation complète sur [npm MotoDB](https://www.npmjs.com/package/motodb).

---
transition: fade-out
---

## Tests

La bibliothèque MotoDB est rigoureusement testée pour garantir son bon fonctionnement. Voici un aperçu de la couverture des tests unitaires :

### `getAllBikes()`

Cette méthode est testée pour s'assurer qu'elle renvoie toutes les motos de la base de données.

### `getAllBikesA2()`

Cette méthode est testée pour vérifier qu'elle renvoie uniquement les motos adaptées aux détenteurs du permis A2.

### `getBikesByBrand(brand)`

Cette méthode est testée avec différents noms de marques pour garantir qu'elle renvoie les modèles appropriés.

### `getBikesByPower(power_hp, tolerance)`

Cette méthode est testée avec différentes valeurs de puissance et de tolérance pour s'assurer qu'elle renvoie les motos correctes en fonction des critères spécifiés.

### `getBikesByYear(year)`

Cette méthode est testée avec différentes années pour garantir qu'elle renvoie les motos lancées avant l'année spécifiée.

La couverture complète des tests unitaires assure la fiabilité de chaque fonctionnalité de la bibliothèque.

---
transition: fade-out
---

## Roadmap

La bibliothèque MotoDB est en constante évolution, et voici un aperçu des fonctionnalités et améliorations prévues pour les prochaines versions :

### Version 1.1.0 (À venir)

- **Fonction de recherche avancée :** Ajout d'une fonction de recherche avancée permettant aux utilisateurs de filtrer les motos par plusieurs critères, tels que la puissance, l'année de lancement et le type de moto.

- **Optimisation des performances :** Optimisation des requêtes et des algorithmes pour améliorer la vitesse et l'efficacité de la bibliothèque, garantissant ainsi une expérience utilisateur plus fluide.

- **Support multilingue :** Ajout de la prise en charge de plusieurs langues pour les messages d'erreur et les retours utilisateur, rendant la bibliothèque plus accessible à un public international.

### Version 1.2.0 (À venir)

- **Intégration de données en temps réel :** Intégration de flux de données en temps réel pour que la bibliothèque puisse mettre à jour les informations sur les motos à mesure qu'elles deviennent disponibles.

- **Filtrage avancé :** Ajout de fonctionnalités de filtrage avancées, y compris la capacité de trier les résultats par différents critères tels que la popularité, le prix et les évaluations des utilisateurs.

- **Compatibilité avec d'autres plateformes :** Développement de versions de la bibliothèque compatibles avec d'autres plateformes, y compris les applications mobiles iOS et Android, pour offrir une expérience utilisateur cohérente sur toutes les plateformes.

Cette roadmap est sujette à modifications et sera mise à jour régulièrement en fonction des retours de la communauté et des besoins des utilisateurs.
