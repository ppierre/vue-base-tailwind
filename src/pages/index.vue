<script setup lang="ts">
import PersonneCard from '@/components/PersonneCard.vue'
import { personnesListe } from '@/personnesListe'
</script>

<template>
  <div>
    <h2 class="text-2xl">Liste les liens</h2>
    <ul>
      <li v-for="(unPersonne, indice) in personnesListe" :key="indice">
        <RouterLink
          class="text-red-600 hover:text-red-400"
          :to="{
            name: 'personnes-id',
            params: { id: indice }
          }"
        >
          {{ unPersonne.nom }}
        </RouterLink>
      </li>
    </ul>
  </div>
</template>
