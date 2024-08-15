<script setup lang="ts">
import { useEventStore } from '@/stores/event'
import { storeToRefs } from 'pinia'

const store = useEventStore()
const { event } = storeToRefs(store)
</script>
<!-- <template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <nav>
        <RouterLink :to="{ name: 'event-detail-view' }">Details</RouterLink>
        <RouterLink :to="{ name: 'event-register-view' }">Register</RouterLink>
        <RouterLink :to="{ name: 'event-edit-view' }">Edit</RouterLink>
    </nav>
      <RouterView :event="event" />
  </div>
</template> -->

<template>
  <div v-if="event">
    <h1>{{ event.title }}</h1>
    <nav class="flex justify-center space-x-4 py-4">
      <RouterLink
        :to="{ name: 'event-detail-view' }"
        class="text-green-600 hover:text-green-800 font-semibold"
      >
        Details 
      </RouterLink>
      <span>|</span>
      <RouterLink
        :to="{ name: 'event-register-view' }"
        class="text-green-600 hover:text-green-800 font-semibold"
      >
        Register 
      </RouterLink>
      <span>|</span>
      <RouterLink
        :to="{ name: 'event-edit-view' }"
        class="text-green-600 hover:text-green-800 font-semibold"
      >
        Edit
      </RouterLink>
    </nav>
    <RouterView :event="event" />
  </div>
</template>
