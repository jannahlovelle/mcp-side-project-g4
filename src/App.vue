<script setup>
import Navbar from '@/components/Navbar.vue'
import Footer from '@/components/Footer.vue'
import { computed } from 'vue'
import { useRoute } from 'vue-router'

const route = useRoute()
const hideNavbar = computed(() => ['/login', '/signup'].includes(route.path))
</script>

<template>
  <div class="min-vh-100 bg-background text-on-background d-flex flex-column justify-content-between">
    <Navbar v-if="!hideNavbar" />
    <router-view />
    <Footer v-if="!hideNavbar" />
  </div>
</template>

<style scoped></style>
