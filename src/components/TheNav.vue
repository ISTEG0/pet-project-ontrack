<script setup>
import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'
import { PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS } from '../constants.js'
import NavItem from './NavItem.vue'

defineProps(['currentPage']);

const emit = defineEmits(['navigate']);

const navItems = {
  [PAGE_TIMELINE]: ClockIcon,
  [PAGE_ACTIVITIES]: ListBulletIcon,
  [PAGE_PROGRESS]: ChartBarIcon
}
</script>

<template>
  <nav class="sticky bottom-0 z-10 bg-white">
    <ul class="flex items-center justify-around border-t">
      <NavItem
        v-for="(icon, page) in navItems"
        v-bind:key="page"
        v-bind:href="`#${page}`"
        v-bind:class="{ 'pointer-events-none bg-gray-200': page === currentPage }"
        v-on:click="emit('navigate', page)"
      >
        <component v-bind:is="icon" class="h-6 w-6" /> {{ page }}
      </NavItem>
    </ul>
  </nav>
</template>
