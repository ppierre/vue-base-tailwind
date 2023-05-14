<script setup lang="ts">
import PersonneCard from '@/components/PersonneCard.vue'
import { personnesListe } from '@/personnesListe'
</script>

<template>
  <div>
    <PersonneCard v-for="unPersonne in personnesListe" :key="unPersonne.nom" v-bind="unPersonne" />
  </div>
</template>
