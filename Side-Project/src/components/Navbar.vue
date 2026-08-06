<script setup>
import { useRoute } from 'vue-router'

const route = useRoute()
</script>

<template>
  <header class="position-fixed top-0 w-100 z-3 bg-background bg-opacity-75 backdrop-blur">
    <div
      class="max-w-1200 mx-auto px-4 d-flex align-items-center justify-content-between neomorph-outset rounded-pill mt-3 py-2 px-md-4"
      style="height: 72px;"
    >
      <router-link to="/" class="d-flex align-items-center gap-2 text-decoration-none cursor-pointer">
        <img
          alt="SkyBook Logo"
          class="object-fit-contain"
          style="height: 32px;"
          src="https://lh3.googleusercontent.com/aida-public/AB6AXuD8mpObndNhO4DzVJT13_bym92YiZ-Von6n5ck1S6z4lE9itINaVMX9oBQTKCXV1REft6KsJpI5jON2ZzJGYpLdw-gSGVVXul0e-oGkDTPBbhWGLO0ZsFWolzOleZ5NXG9BLe9b_baMtlSRU4VlvltVOqojq6-5J5-V9AEQrlxSuhEMnWOz8Vjrhb5NXSQIJ6ghPOMcNuV2oq-Fp7OFOrifS2lxi22WS1JE1LMj3Y6IRR5OwGVw4Ot73LJFhMHcMVrBogeFZT5AquE"
        />
        <span class="font-headline fs-4 text-primary tracking-tight"
          >SkyBook</span
        >
      </router-link>

      <nav class="d-none d-md-flex align-items-center gap-2">
        <router-link
          to="/"
          class="text-decoration-none px-3 py-2 rounded-pill small transition-all"
          :class="
            route.path === '/'
              ? 'neomorph-inset text-primary fw-bold'
              : 'text-on-surface-variant hover-primary'
          "
        >
          Home
        </router-link>

        <router-link
          to="/search-results"
          class="text-decoration-none px-3 py-2 rounded-pill small transition-all"
          :class="
            route.path === '/search-results'
              ? 'neomorph-inset text-primary fw-bold'
              : 'text-on-surface-variant hover-primary'
          "
        >
          Search Flights
        </router-link>

        <router-link
          to="/my-bookings"
          class="text-decoration-none px-3 py-2 rounded-pill small transition-all"
          :class="
            route.path === '/my-bookings'
              ? 'neomorph-inset text-primary fw-bold'
              : 'text-on-surface-variant hover-primary'
          "
        >
          Manage Booking
        </router-link>

        <router-link
          to="/manage-flights"
          class="text-decoration-none px-3 py-2 rounded-pill small transition-all"
          :class="
            route.path.startsWith('/manage-flights') || route.path.startsWith('/add-flight')
              ? 'neomorph-inset text-primary fw-bold'
              : 'text-on-surface-variant hover-primary'
          "
        >
          Manage Flights
        </router-link>

        <router-link
          to="/about-us"
          class="text-decoration-none px-3 py-2 rounded-pill small transition-all"
          :class="
            route.path === '/about-us'
              ? 'neomorph-inset text-primary fw-bold'
              : 'text-on-surface-variant hover-primary'
          "
        >
          About
        </router-link>
      </nav>

      <div class="d-flex align-items-center gap-2">
        <router-link
          to="/login"
          class="btn border-0 neomorph-btn-primary px-3 py-2 rounded-3 small text-secondary hover-primary text-decoration-none"
        >
          Login
        </router-link>
        <router-link
          to="/signup"
          class="btn border-0 bg-primary text-on-primary px-3 py-2 rounded-3 small neomorph-btn-primary text-decoration-none"
        >
          Sign Up
        </router-link>
        <router-link
          to="/my-bookings"
          class="rounded-circle bg-primary d-flex align-items-center justify-content-center ms-1 text-decoration-none"
          style="width: 32px; height: 32px;"
        >
          <span class="material-symbols-outlined text-on-primary" style="font-size: 18px;"
            >person</span
          >
        </router-link>
      </div>
    </div>
  </header>
</template>

<style scoped>
.backdrop-blur {
  backdrop-filter: blur(8px);
}
.hover-primary:hover {
  color: var(--primary) !important;
}
.tracking-tight {
  letter-spacing: -0.02em;
}
</style>
