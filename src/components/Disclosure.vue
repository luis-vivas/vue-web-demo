<script setup lang="ts">

import { ref } from 'vue'
const open = ref<Boolean>(false)
function toggle() {
  open.value = !open.value
}

</script>

<template>
  <div class="px-8 py-4 bg-teal-900 rounded-md">
    <slot :open="open" />
    <DisclosureButton @toggle-event="toggle">
      Trigger button
    </DisclosureButton>
  </div>
</template>
