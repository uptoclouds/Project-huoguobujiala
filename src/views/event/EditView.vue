<template>
  <div v-if="medalEvent">
    <h3 class="medal-stats-title">Statistics on the number of medals in each event:</h3>
    <pre>{{ medalEvent.medals }}</pre>
  </div>
  <div v-else>
    <p>No medal data found for the given event.</p>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';
import type {  Event, MedalEvent } from '@/type';
import EventService from '@/services/EventService'; 
const props = defineProps<{
  event: Event;
}>();

const medalEvent = ref<MedalEvent | undefined>();

onMounted(async () => {
  medalEvent.value = await EventService.getMedalEventById(props.event.id);
});
</script>

<style scoped>
.medal-stats-title {
  color: #333; 
  font-size: 1.5em; 
  font-weight: bold; 
  margin-top: 0.5em; 
  margin-bottom: 1em; 
}
</style>