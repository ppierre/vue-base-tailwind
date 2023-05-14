<script setup lang="ts">
import PersonneCard from '@/components/PersonneCard.vue'
import { personnesListe } from '@/personnesListe'
import type { Personne } from '@/types'

const props = defineProps<{ id: string }>()

const unPersonne: Personne = personnesListe[Number(props.id)]
</script>
<template>
  <div>
    <h2 class="text-xl">Une personne</h2>
    <PersonneCard v-bind="unPersonne" />
  </div>
</template>
