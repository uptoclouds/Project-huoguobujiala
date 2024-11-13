<script setup lang="ts">
import { toRefs, defineProps } from 'vue'
import { type Event } from '@/type'
const props = defineProps<{
  event: Event
  id: 'String'
}>()
const { event } = toRefs(props)
</script>
<template>
  <p>id: {{ event.id }} rank: {{ event.rank }}</p>
  <p>TrankChangeType:  {{ event.rankChangeType }}</p>
  <p>The Number of GoldMedal : {{ event.goldMedalNum }}</p>
  <p>The Number of SilverMedal : {{ event.silverMedalNum }}</p>
  <p>The Number of BronzeMedal : {{ event.bronzeMedalNum }}</p>
</template>