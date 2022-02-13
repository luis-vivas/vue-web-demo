<template>
  <Navbar />
  <main class="px-4 py-10 text-center text-gray-700 dark:text-gray-200">
    <router-view />
    <Footer />
    <div class="mt-5 mx-auto text-center opacity-25 text-sm">
      [Home Layout]
    </div>
    <Disclosure v-slot="{ open }">
      <div v-if="open">
        Opened
      </div>
      <div v-else>
        Closed
      </div>
      <div :hidden="!open">
        Content Is Opened ({{ open }})
      </div>
    </Disclosure>
  </main>
</template>
