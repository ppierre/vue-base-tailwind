<script setup lang="ts">
//
</script>

<template>
  <header>
    <h1 class="text-4xl">Test</h1>
    <RouterLink class="text-red-600 hover:text-red-400" to="/">Retour accueil</RouterLink>
  </header>

  <main>
    <Suspense>
      <RouterView />
    </Suspense>
  </main>
</template>
