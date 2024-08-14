<template>
    <div class="event-details text-right text-base p-5 w-64 cursor-pointer border border-gray-700 mb-2">
      <span class="block">{{ event.category }}</span>
      <span class="block">{{ event.organizer }}</span>
    </div>
  </template>
  
  <script setup lang="ts">
  import { defineProps } from 'vue'
  import { type Event } from '@/types'
  
  defineProps<{ event: Event }>()
  </script>
  
  <style scoped>
  /* .event-details {
    text-align: right;
    font-size: 16px;
    padding: 20px;
    width: 250px;
    cursor: pointer;
    border: 1px solid #39495c;
    margin-bottom: 10px;
  }
  
  .category, .organizer {
    display: block;
  } */
  </style>
  