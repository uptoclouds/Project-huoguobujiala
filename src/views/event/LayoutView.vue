<script setup lang="ts">
import { useEventStore } from '@/stores/event'
import { storeToRefs } from 'pinia'

const store = useEventStore()
const { event } = storeToRefs(store)
</script>
<template>
  <div v-if="event">
    <h1>{{ event.countryName }}</h1>
    <nav>
      <RouterLink :to="{ name: 'event-detail-view' }"> Country Details </RouterLink>
      |
      <RouterLink :to="{ name: 'event-register-view' }"> Comments </RouterLink>
      |
      <RouterLink :to="{ name: 'event-edit-view' }"> Details of the sports program </RouterLink>
    </nav>
    <RouterView :event="event" />
  </div>
</template>