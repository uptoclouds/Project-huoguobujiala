<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>
  <SpeedInsights />
  <div class="text-center font-sans text-gray-700 antialias">
    <header>
      <h1>Olympic medal table</h1>
      <div class="wrapper">
        <nav class="py-6">
          <RouterLink class="font-bold text-gray-700" exact-active-class="text-green-500" :to="{ name: 'event-list-view' }">Country</RouterLink> |
          <RouterLink class="font-bold text-gray-700" exact-active-class="text-green-500" :to="{ name: 'about' }">About</RouterLink>
        </nav>
      </div>
    </header>

    <RouterView />
  </div>
</template>
