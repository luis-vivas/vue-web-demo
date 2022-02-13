<script setup lang="ts">
const emit = defineEmits<{
  (e: 'toggle-event'): void
}>()
</script>

<template>
  <button class="btn" @click="emit('toggle-event')">
    <slot>
      defaultcontent
    </slot>
  </button>
</template>
