# Test de type TypeScript avec composant

nécessite Vue 3.3 ; si probléme de dépendance, faire :

```
npm i -f
```

# COURS

# Simple type/composant en Vue3/TypeScript

## Synposys

- Liste avec répetions
- Boucle sur des données (tableau d'objets)
- Type d'un objet
  - Et donc type du tableau
- Composant affichant un objet (une instance)
  - Rendre le composant Vue paramétrique (reçoit l'instance en paramétre)
- "Appeler" (afficher) le composant Vue en lui passant une insantance (stocké dans une variable)
- Afficher le compsant Vue dans la boucle
- Manipuler les données avant de les afficher :
  - [`sort`][sort] : trier
  - [`slice`][slice] : partie
  - [`filter`][filter]: filtrer
  - [`map`][map] : transformer
  - ...

## Liste avec répetions

[Github](https://github.com/ppierre/vue-base-tailwind/blob/01-liste-avec-r%C3%A9petions/src/App.vue#L11-L25)

```html
<div class="personne-card border-2 p-1">
  <p>nom : Jean</p>
  <p>age : 22</p>
  <p>marié : non</p>
</div>
<div class="personne-card bd-1 border-2">
  <p>nom : Paul</p>
  <p>age : 25</p>
  <p>marié : oui</p>
</div>
<div class="personne-card bd-1 border-2">
  <p>nom : Renée</p>
  <p>age : 33</p>
  <p>marié : non</p>
</div>
```

## Boucle

Github: [données](https://github.com/ppierre/vue-base-tailwind/blob/02-boucle/src/App.vue#L2-L6) et [template](https://github.com/ppierre/vue-base-tailwind/blob/01-liste-avec-r%C3%A9petions/src/App.vue#L11-L25)
TODO:explication

```html
<script setup lang="ts">
  const personnesListe = [
    { nom: 'Jean', age: 22, marie: false },
    { nom: 'Paul', age: 25, marie: true },
    { nom: 'Renée', age: 33, marie: false }
  ]
</script>

<template>
  <div v-for="personne in personnesListe" class="personne-card border-2 p-1">
    <p>nom : {{ personne.nom }}</p>
    <p>age : {{ personne.age }}</p>
    <p>marié : {{ personne.marie ? 'oui' : 'non' }}</p>
  </div>
</template>
```

## Type

### Type dans le même fichier

[Github](https://github.com/ppierre/vue-base-tailwind/blob/03-type-local/src/App.vue#L2-L6)
TODO:explication

Dans `<script setup lang="ts">` :

```ts
interface Personne {
  nom: string
  age: number
  marie: boolean
}
const personnesListe: Personne[] = [
  { nom: 'Jean', age: 22, marie: false },
  { nom: 'Paul', age: 25, marie: true },
  { nom: 'Renée', age: 33, marie: false }
```

### Type dans un fichier séparé

[`/src/types.ts`](https://github.com/ppierre/vue-base-tailwind/blob/04-type-fichier-sp%C3%A9ar%C3%A9/src/types.ts#L1)

```ts
export interface Personne {
  nom: string
  age: number
  marie: boolean
}
```

Dans [`<script setup lang="ts">`](https://github.com/ppierre/vue-base-tailwind/blob/04-type-fichier-sp%C3%A9ar%C3%A9/src/App.vue#L2) :

```ts
import type { Personne } from './types'

const personnesListe: Personne[] = [
  { nom: 'Jean', age: 22, marie: false },
  { nom: 'Paul', age: 25, marie: true },
  { nom: 'Renée', age: 33, marie: false }
]
```

## Composant Vue

TODO:explication

### Conposant sans paramétre

`/src/components/PersonneCard.vue`

```html
<template>
  <div class="personne-card border-2 p-1">
    <p>nom : Jean</p>
    <p>age : 22</p>
    <p>marié : non</p>
  </div>
</template>
```

### Composant avec paramétre

[`/src/components/PersonneCard.vue`](https://github.com/ppierre/vue-base-tailwind/blob/05-usage-composant/src/components/PersonneCard.vue#L1)

```html
<script setup lang="ts">
  import type { Personne } from '@/types'

  defineProps<Personne>()
</script>
<template>
  <div class="personne-card border-2 p-1">
    <p>nom : {{ nom }}</p>
    <p>age : {{ age }}</p>
    <p>marié : {{ marie ? 'oui' : 'non' }}</p>
  </div>
</template>
```

## Usage composant

[Github](https://github.com/ppierre/vue-base-tailwind/blob/05-usage-composant/src/App.vue#L18-L29)
TODO:explication

```html
<!-- Passe 'props' individuelles -->
<PersonneCard nom="Paul" :age="25" marie />
<!-- Passe un objet instance de "Personne" -->
<PersonneCard
  v-bind="{
        nom: 'Renée',
        age: 33,
        marie: false
      }"
/>
<!-- Passe un élément du tableau de "Personne" -->
<PersonneCard v-bind="personnesListe[0]" />
```

## Usage dans une boucle

[GitHub](https://github.com/ppierre/vue-base-tailwind/blob/06-boucle-composant/src/App.vue#L18)
TODO:explication

```html
<PersonneCard v-for="unPersonne in personnesListe" :key="unPersonne.nom" v-bind="unPersonne" />
```

## Traitement données

TODO:explication et lien code

- [`sort`][sort] : trier
- [`slice`][slice] : partie
- [`filter`][filter]: filtrer
- [`map`][map] : transformer

[sort]: https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/sort
[slice]: https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/slice
[filter]: https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/filter
[map]: https://developer.mozilla.org/fr/docs/Web/JavaScript/Reference/Global_Objects/Array/map
