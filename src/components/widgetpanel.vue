<script setup lang="ts">
import { ref } from 'vue'
const open = ref(false)
</script>

<template>
  <div class="px-8 py-4 bg-teal-900 rounded-md">
    <button class="btn" aria-expanded="true" @click="open = !open">
      Trigger
    </button>
    <transition enter-active-class="transition ease-out duration-100" enter-from-class="transform opacity-0 scale-95" enter-to-class="transform opacity-100 scale-100" leave-active-class="transition ease-in duration-75" leave-from-class="transform opacity-100 scale-100" leave-to-class="transform opacity-0 scale-95">
      <div :hidden="!open">
        Content {{ open }}
      </div>
    </transition>
  </div>
</template>
