<script setup>
import { ref, onMounted } from 'vue'
import EventServices from '@/Services/eventServices.js'

const props = defineProps({
  id: {
    required: true
  }
})

const event = ref(null)

onMounted(() => {
  EventServices.getEvent(props.id)
    .then((res) => (event.value = res.data))
    .catch((err) => console.log(err))
})
</script>

<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <p>{{ event.time }} on {{ event.date }} @ {{ event.location }}</p>
    <p>{{ event.description }}</p>
  </div>
</template>
