<script setup lang="ts">
import { ref} from 'vue';
import { useRouter } from 'vue-router';
import { useMessageStore } from '@/stores/message';
import { type Event } from '@/types';

const props = defineProps<{ 
  event: Event
  id: String
}>()
// eslint-disable-next-line @typescript-eslint/no-unused-vars
const router = useRouter();
const store = useMessageStore();
const showMessage = ref(false);
const flashMessage = ref('');

const editEvent = () => {
  store.updateMessage('The data has been updated');
  setTimeout(() => {
    store.resetMessage();
  }, 3000);
  router.push({ name: 'event-detail-view', params: { id: props.event.id }});
};
</script>

<!-- <template>
  <div>
    <p>Edit event here</p>
    <button @click="editEvent">Edit</button>
    <div v-if="showMessage">
      {{ flashMessage }}
    </div>
  </div>
</template> -->

<template>
  <p class="text-lg font-semibold mb-4"> Edit event here </p>
  <button
    @click="editEvent"
    class="bg-green-600 text-white font-bold py-2 px-4 rounded hover:bg-green-800 focus:outline-none focus:ring-2 focus:ring-green-600 focus:ring-opacity-50"
  >
    Edit
  </button>
</template>
