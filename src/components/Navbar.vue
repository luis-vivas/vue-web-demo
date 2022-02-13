<script setup lang="ts">
import { ref } from 'vue'
const open = ref(false)
const toggleMenu = () => { open.value = !open.value }

const navigation = [
  { name: 'Dashboard', href: '#', current: true },
  { name: 'Team', href: '#', current: false },
  { name: 'Projects', href: '#', current: false },
  { name: 'Calendar', href: '#', current: false },
]
</script>

<template>
  <nav class="relative z-1 bg-gray-100 dark:bg-gray-800 text-gray-700 dark:text-gray-200">
    <div class="bg-[inherit] max-w-screen-xl mx-auto px-2 sm:px-6 lg:px-8">
      <div class="relative flex items-center justify-between h-16">
        <div class="absolute inset-y-0 left-0 flex items-center sm:hidden">
          <!-- Mobile menu button-->
          <MobileMenuButton @toggle-event="toggleMenu">
            <span class="sr-only">Open main menu</span>
            <carbon-menu v-if="!open" class="block h-6 w-6" aria-hidden="true" />
            <carbon-close v-else class="block h-6 w-6" aria-hidden="true" />
          </MobileMenuButton>
        </div>

        <div class="flex-1 flex items-center justify-center sm:items-stretch sm:justify-start">
          <div class="flex-shrink-0 flex items-center">
            <img class="block h-8 w-auto" src="/star.png" alt="star-logo">
            <span class="ml-3 text-2xl font-bold hidden sm:block">Star</span>
          </div>
          <div class="hidden sm:block sm:ml-6">
            <div class="flex space-x-4">
              <a v-for="item in navigation" :key="item.name" :href="item.href" :class="[item.current ? 'btn-link opacity-100 bg-gray-300 dark:bg-gray-900 dark:text-white' : 'btn-link']" :aria-current="item.current ? 'page' : undefined">{{ item.name }}</a>
            </div>
          </div>
        </div>
        <div class="absolute inset-y-0 right-0 flex items-center pr-2 sm:static sm:inset-auto sm:ml-6 sm:pr-0">
          <button type="button" class="icon-btn icon-btn-ring p-1">
            <span class="sr-only">View notifications</span>
            <carbon-shopping-cart class="font-bold block h-6 w-6" aria-hidden="true" />
          </button>

          <button class="hidden sm:block btn ml-3 relative">
            Login
          </button>
          <!-- Profile dropdown -->
          <div class="ml-3 relative">
            <button class="icon-btn icon-btn-ring flex">
              <span class="sr-only">Open user menu</span>
              <img class="h-8 w-8 rounded-full" src="/logo.png" alt="profile">
            </button>
          </div>
        </div>
      </div>
    </div>
    <!-- Mobile Menu -->
    <transition
      enter-active-class="transition-all ease-out duration-200"
      enter-from-class="transform opacity-0 -translate-y-full"
      enter-to-class="transform opacity-100 translate-y-0"
      leave-active-class="transition-all ease-out duration-200"
      leave-from-class="transform opacity-100 translate-y-0"
      leave-to-class="transform opacity-0 -translate-y-full"
    >
      <div v-if="open" class="sm:hidden origin-top absolute -z-2 overflow-hidden bg-gray-100 dark:bg-gray-800 w-full">
        <div class="px-2 pt-2 pb-3 space-y-1">
          <a v-for="item in navigation" :key="item.name" as="a" :href="item.href" :class="[item.current ? 'btn-link opacity-100 bg-gray-300 dark:bg-gray-900 dark:text-white' : 'btn-link']" :aria-current="item.current ? 'page' : undefined">{{ item.name }}</a>
        </div>
      </div>
    </transition>
  </nav>
</template>
