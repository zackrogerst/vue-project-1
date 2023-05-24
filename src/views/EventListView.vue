<script setup>
import EventCard from '@/components/EventCard.vue'
import EventServices from '@/Services/eventServices.js'
import { ref, onMounted } from 'vue'

const events = ref(null)

onMounted(() => {
  EventServices.getEvents()
    .then((res) => {
      console.log('events', res.data)
      events.value = res.data
    })
    .catch((err) => console.log(err))
})
</script>

<template>
  <div class="events">
    <EventCard v-for="event in events" :key="event.id" :event="event" />
  </div>
</template>

<style scoped>
.events {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
