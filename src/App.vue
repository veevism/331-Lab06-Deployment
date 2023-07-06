<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import { useMessageStore } from './stores/message';
import { storeToRefs } from 'pinia';

const store = useMessageStore()
const { message } = storeToRefs(store)

</script>

<template>
  <header class="max-h-screen leading-normal">
    <div id="flashMessage" v-if="message" class="animate-yellowfade">
      <h4 class="text-lg">{{ message }}</h4>
    </div>
    <nav class="p-8">
      <RouterLink :to="{ name: 'event-list' }" class="font-bold text-gray-700 hover:text-green-500">Home</RouterLink>
      <RouterLink :to="{ name: 'about' }" class="font-bold text-gray-700 hover:text-green-500">About</RouterLink>
    </nav>
  </header>
  <RouterView />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

@keyframes yellowfade {
  from {
    background: yellow;
  }

  to {
    background: transparent;
  }
}

.animate-yellowfade {
  animation: yellowfade 3s ease-in-out;
}
</style>
