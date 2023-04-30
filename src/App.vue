<script setup lang="ts">
import PersonneCard from './components/PersonneCard.vue'
import type { Personne } from './types'

const personnesListe: Personne[] = [
  { nom: 'Jean', age: 22, marie: false },
  { nom: 'Paul', age: 25, marie: true },
  { nom: 'Renée', age: 33, marie: false }
]
</script>

<template>
  <header>
    <h1 class="text-4xl">Test</h1>
  </header>

  <main>
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
    <p>
      Lorem ipsum dolor sit amet, consectetur adipisicing elit. Tempora recusandae et dolorem odit
      beatae illo labore, praesentium quidem nulla eveniet, at voluptatem incidunt. Eaque explicabo,
      vitae quibusdam vero quod atque.
    </p>
  </main>
</template>
