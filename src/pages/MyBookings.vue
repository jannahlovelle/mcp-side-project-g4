<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()
const activeTab = ref('Upcoming')
</script>

<template>
  <main class="w-100 pt-5 bg-background pb-5 mt-5">
    <div class="max-w-1200 mx-auto px-3 my-4 d-flex flex-column gap-4">
      <div class="d-flex flex-column gap-2">
        <h1 class="font-display display-5 text-primary mb-0">My Bookings</h1>
        <p class="font-body fs-6 text-on-surface-variant mb-0" style="max-width: 650px;">
          Manage your upcoming flights, review past itineraries, and keep track of your travel history seamlessly.
        </p>
      </div>

      <!-- Tabs -->
      <div class="d-flex gap-2 neomorph-inset p-2 rounded-4 w-auto me-auto mb-3">
        <button
          @click="activeTab = 'Upcoming'"
          :class="
            activeTab === 'Upcoming'
              ? 'neomorph-outset bg-surface text-primary font-headline'
              : 'text-on-surface-variant hover-primary'
          "
          class="btn border-0 px-4 py-2 rounded-3 font-headline small transition-all cursor-pointer"
        >
          Upcoming
        </button>
        <button
          @click="activeTab = 'Past'"
          :class="
            activeTab === 'Past'
              ? 'neomorph-outset bg-surface text-primary font-headline'
              : 'text-on-surface-variant hover-primary'
          "
          class="btn border-0 px-4 py-2 rounded-3 font-headline small transition-all cursor-pointer"
        >
          Past Flights
        </button>
        <button
          @click="activeTab = 'Cancelled'"
          :class="
            activeTab === 'Cancelled'
              ? 'neomorph-outset bg-surface text-primary font-headline'
              : 'text-on-surface-variant hover-primary'
          "
          class="btn border-0 px-4 py-2 rounded-3 font-headline small transition-all cursor-pointer"
        >
          Cancelled
        </button>
      </div>

      <!-- Booking List -->
      <div v-if="activeTab === 'Upcoming'" class="d-flex flex-column gap-4">
        <!-- Card 1 -->
        <div
          class="neomorph-outset rounded-4 p-4 d-flex flex-column flex-md-row gap-4 bg-surface-container-lowest position-relative overflow-hidden"
        >
          <div class="d-flex flex-column gap-1 shrink-0 border-start border-3 border-secondary ps-3 py-1" style="min-width: 150px;">
            <div class="d-flex align-items-center gap-2">
              <span class="rounded-circle bg-secondary" style="width: 8px; height: 8px;"></span>
              <span class="small text-uppercase text-secondary fw-bold" style="font-size: 11px;">Confirmed</span>
            </div>
            <div class="font-headline fs-6 text-on-surface">Oct 14, 2026</div>
            <div class="small text-on-surface-variant">Booking Ref: #SB-98A4X</div>
          </div>

          <div class="flex-grow-1 d-flex flex-column justify-content-center">
            <div class="d-flex align-items-center justify-content-between w-100 position-relative">
              <div class="d-flex flex-column gap-1 w-33">
                <span class="font-headline fs-2 text-primary">JFK</span>
                <span class="small text-on-surface-variant text-truncate">New York, USA</span>
                <span class="font-headline fs-6 text-on-surface mt-1">08:45 AM</span>
              </div>

              <div class="flex-grow-1 d-flex flex-column align-items-center justify-content-center px-3 position-relative">
                <div class="w-100 border-top position-absolute top-50 translate-middle-y"></div>
                <span
                  class="material-symbols-outlined text-primary text-[32px] neomorph-outset bg-surface-container-lowest rounded-circle p-2 position-relative z-1"
                  style="transform: rotate(90deg);"
                  >flight</span
                >
                <span class="small text-on-surface-variant mt-2 text-center" style="font-size: 11px;">5h 30m • Non-stop</span>
              </div>

              <div class="d-flex flex-column gap-1 w-33 align-items-end text-end">
                <span class="font-headline fs-2 text-primary">LHR</span>
                <span class="small text-on-surface-variant text-truncate">London, UK</span>
                <span class="font-headline fs-6 text-on-surface mt-1">07:15 PM</span>
              </div>
            </div>
          </div>

          <div
            class="d-flex flex-row flex-md-column gap-3 align-items-center align-items-md-end justify-content-center border-md-start ps-md-4 pt-3 pt-md-0"
          >
            <button
              @click="router.push('/booking-confirmed')"
              class="btn border-0 neomorph-btn-primary bg-primary text-on-primary font-headline small px-4 py-2 rounded-3 w-100 w-md-auto cursor-pointer"
            >
              View Details
            </button>
            <button
              class="btn border-0 px-4 py-2 rounded-3 font-headline small text-danger w-100 w-md-auto cursor-pointer"
            >
              Cancel Booking
            </button>
          </div>
        </div>

        <!-- Card 2 -->
        <div
          class="neomorph-outset rounded-4 p-4 d-flex flex-column flex-md-row gap-4 bg-surface-container-lowest position-relative overflow-hidden"
        >
          <div class="d-flex flex-column gap-1 shrink-0 border-start border-3 border-warning ps-3 py-1" style="min-width: 150px;">
            <div class="d-flex align-items-center gap-2">
              <span class="rounded-circle bg-warning" style="width: 8px; height: 8px;"></span>
              <span class="small text-uppercase text-warning fw-bold" style="font-size: 11px;">Action Needed</span>
            </div>
            <div class="font-headline fs-6 text-on-surface">Nov 02, 2026</div>
            <div class="small text-on-surface-variant">Booking Ref: #SB-22C9Y</div>
          </div>

          <div class="flex-grow-1 d-flex flex-column justify-content-center">
            <div class="d-flex align-items-center justify-content-between w-100 position-relative">
              <div class="d-flex flex-column gap-1 w-33">
                <span class="font-headline fs-2 text-primary">SFO</span>
                <span class="small text-on-surface-variant text-truncate">San Francisco, USA</span>
                <span class="font-headline fs-6 text-on-surface mt-1">11:20 AM</span>
              </div>

              <div class="flex-grow-1 d-flex flex-column align-items-center justify-content-center px-3 position-relative">
                <div class="w-100 border-top position-absolute top-50 translate-middle-y"></div>
                <span
                  class="material-symbols-outlined text-primary text-[32px] neomorph-outset bg-surface-container-lowest rounded-circle p-2 position-relative z-1"
                  style="transform: rotate(90deg);"
                  >flight</span
                >
                <span class="small text-on-surface-variant mt-2 text-center" style="font-size: 11px;">14h 45m • 1 Stop</span>
              </div>

              <div class="d-flex flex-column gap-1 w-33 align-items-end text-end">
                <span class="font-headline fs-2 text-primary">HND</span>
                <span class="small text-on-surface-variant text-truncate">Tokyo, Japan</span>
                <span class="font-headline fs-6 text-on-surface mt-1">04:05 PM</span>
              </div>
            </div>

            <div class="neomorph-inset bg-warning-subtle p-2 rounded-3 mt-3 d-flex align-items-center gap-2">
              <span class="material-symbols-outlined text-warning">info</span>
              <span class="small text-on-surface">Please select your seats before check-in opens.</span>
            </div>
          </div>

          <div
            class="d-flex flex-row flex-md-column gap-3 align-items-center align-items-md-end justify-content-center border-md-start ps-md-4 pt-3 pt-md-0"
          >
            <button
              @click="router.push('/booking-confirmed')"
              class="btn border-0 neomorph-btn-primary bg-primary text-on-primary font-headline small px-4 py-2 rounded-3 w-100 w-md-auto cursor-pointer"
            >
              View Details
            </button>
            <button
              class="btn border-0 px-4 py-2 rounded-3 font-headline small text-danger w-100 w-md-auto cursor-pointer"
            >
              Cancel Booking
            </button>
          </div>
        </div>
      </div>

      <div v-else class="neomorph-outset rounded-4 p-5 text-center text-on-surface-variant">
        No {{ activeTab.toLowerCase() }} bookings found.
      </div>
    </div>
  </main>
</template>

<style scoped>
.hover-primary:hover {
  color: var(--primary) !important;
}
.w-33 {
  width: 33%;
}
</style>
