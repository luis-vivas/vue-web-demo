<script setup lang="ts">
const emit = defineEmits<{
  (e: 'toggle-event'): void
}>()
</script>
<template>
  <button class="icon-btn btn-link btn-ring-inset p-2" @click="emit('toggle-event')">
    <slot>
      defaultcontent
    </slot>
  </button>
</template>
