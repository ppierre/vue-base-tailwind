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
