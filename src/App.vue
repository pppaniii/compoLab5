<script setup lang="ts">
import { RouterLink, RouterView, useRoute, useRouter } from 'vue-router'
import { useMessageStore } from './stores/message';
import { storeToRefs } from 'pinia';
const store = useMessageStore()
const { message } = storeToRefs(store)
import { ref } from 'vue'
import { SpeedInsights } from "@vercel/speed-insights/vue"

const pageSizes = [1, 2, 4, 6, 8, 10]
const pageSize = ref(pageSizes[1])
const router = useRouter()
const route = useRoute()

const updatePageSize = () => {
  router.push({ 
    name: 'event-list-view',
    query: { ...route.query, pageSize: pageSize.value, page: 1 }
  })
}

if (route.query.pageSize) {
  pageSize.value = parseInt(route.query.pageSize.toString())
}
</script>

<template>
  <SpeedInsights />
  <div class="text-center font-sans text-gray-700 antialias">
    <header>
      <div id="flashMessage" class="animate-fade" v-if="message">
        <h4>{{ message }}</h4>
      </div>
      <h1>Deploy with Versal</h1>
      <div class="wrapper">
        <nav>
          <nav class="py-6">
            <RouterLink class="font-bold text-gray-700" exact-active-class="text-green-500" :to="{ name: 'event-list-view'}">Event</RouterLink> |
            <RouterLink class="font-bold text-gray-700" exact-active-class="text-green-500" :to="{ name: 'about'}">About</RouterLink> |
            <RouterLink class="font-bold text-gray-700" exact-active-class="text-green-500" :to="{ name: 'Student'}">Student</RouterLink>
          </nav>
        </nav>
        <!-- Page size selection -->
        <div class="mt-4">
          <label class="mr-2">Set Page Size: </label>
          <span v-for="size in [1, 2, 3, 4, 5, 6]" :key="size" class="mr-2">
            <RouterLink
              class="text-gray-700 hover:text-green-500"
              exact-active-class="text-green-500"
              :to="{ name: 'event-list-view', query: { ...route.query, pageSize: size } }"
            >
              {{ size }}
            </RouterLink>
          </span>
          <!-- <label for="page-size">Event per page</label>
          <select id="page-size" v-model="pageSize" @change="updatePageSize">
            <option v-for="size in pageSizes" :key="size" :value="size">{{ size }}</option>
          </select> -->
        </div>
      </div>
    </header>
    <RouterView />
  </div>
</template>

<style>


nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

h2 {
  font-size: 20px;
}

</style>
