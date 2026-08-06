<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const flightType = ref('one-way')
const origin = ref('New York (JFK)')
const destination = ref('Tokyo (HND)')
const travelDate = ref('2026-08-15')
const travelers = ref('1 Adult, Economy')

const swapCities = () => {
  const temp = origin.value
  origin.value = destination.value
  destination.value = temp
}

const handleSearch = () => {
  router.push({
    path: '/search-results',
    query: {
      from: origin.value,
      to: destination.value,
      date: travelDate.value
    }
  })
}
</script>

<template>
  <main class="w-100 pt-5 bg-background pb-5 mt-5">
    <div class="max-w-1200 mx-auto px-3 d-flex flex-column gap-5 mb-5">
      <!-- Hero Section -->
      <section class="w-100 position-relative d-flex flex-column flex-md-row align-items-center gap-4 pt-4">
        <div class="w-100 w-md-50 d-flex flex-column z-1">
          <h1 class="font-display display-4 text-on-background mb-3">
            Where will the <br />
            <span class="text-primary position-relative d-inline-block">
              sky take you?
              <span
                class="position-absolute bottom-0 start-0 w-100 rounded-pill opacity-50"
                style="height: 4px; background: linear-gradient(90deg, var(--primary), transparent);"
              ></span>
            </span>
          </h1>
          <p class="font-body fs-5 text-on-surface-variant mb-4" style="max-width: 450px;">
            Experience weightless travel booking. Find flights, manage itineraries, and explore destinations with zero friction.
          </p>

          <!-- Flight Search Card -->
          <form
            @submit.prevent="handleSearch"
            class="neomorph-outset bg-surface rounded-4 p-4 d-flex flex-column gap-3 w-100 position-relative overflow-hidden"
          >
            <div
              class="position-absolute rounded-circle blur-3"
              style="top: -40px; right: -40px; width: 160px; height: 160px; background: rgba(0, 94, 163, 0.05); pointer-events: none;"
            ></div>

            <div class="d-flex gap-3 mb-2">
              <button
                type="button"
                @click="flightType = 'one-way'"
                :class="
                  flightType === 'one-way'
                    ? 'neomorph-inset bg-surface text-primary fw-bold'
                    : 'text-on-surface-variant hover-primary'
                "
                class="btn border-0 rounded-pill px-3 py-2 small d-flex align-items-center gap-2 transition-all"
              >
                <span
                  class="material-symbols-outlined"
                  style="font-size: 16px; font-variation-settings: 'FILL' 1"
                  >flight_takeoff</span
                >
                One Way
              </button>
              <button
                type="button"
                @click="flightType = 'round-trip'"
                :class="
                  flightType === 'round-trip'
                    ? 'neomorph-inset bg-surface text-primary fw-bold'
                    : 'text-on-surface-variant hover-primary'
                "
                class="btn border-0 rounded-pill px-3 py-2 small d-flex align-items-center gap-2 transition-all"
              >
                <span class="material-symbols-outlined" style="font-size: 16px;">sync_alt</span>
                Round Trip
              </button>
            </div>

            <div class="row g-3">
              <div class="col-12 col-md-6 d-flex flex-column gap-1">
                <label class="small text-uppercase text-on-surface-variant ps-2 fw-bold" style="font-size: 11px;">From</label>
                <div
                  class="neomorph-inset bg-surface rounded-3 d-flex align-items-center px-3 gap-2"
                  style="height: 48px;"
                >
                  <span class="material-symbols-outlined text-outline-variant">location_on</span>
                  <input
                    v-model="origin"
                    class="bg-transparent border-0 w-100 outline-none font-body text-on-surface"
                    placeholder="Departure City"
                    type="text"
                  />
                </div>
              </div>

              <div class="col-12 col-md-6 d-flex flex-column gap-1 position-relative">
                <div
                  @click="swapCities"
                  class="position-absolute z-3 d-none d-md-flex rounded-circle neomorph-outset bg-surface align-items-center justify-center cursor-pointer text-on-surface-variant hover-primary"
                  style="left: -16px; top: 32px; width: 32px; height: 32px;"
                >
                  <span class="material-symbols-outlined" style="font-size: 18px;">swap_horiz</span>
                </div>
                <label class="small text-uppercase text-on-surface-variant ps-2 fw-bold" style="font-size: 11px;">To</label>
                <div
                  class="neomorph-inset bg-surface rounded-3 d-flex align-items-center px-3 gap-2"
                  style="height: 48px;"
                >
                  <span class="material-symbols-outlined text-outline-variant">flight_land</span>
                  <input
                    v-model="destination"
                    class="bg-transparent border-0 w-100 outline-none font-body text-on-surface"
                    placeholder="Destination City"
                    type="text"
                  />
                </div>
              </div>
            </div>

            <div class="row g-3">
              <div class="col-12 col-md-6 d-flex flex-column gap-1">
                <label class="small text-uppercase text-on-surface-variant ps-2 fw-bold" style="font-size: 11px;">Date</label>
                <div
                  class="neomorph-inset bg-surface rounded-3 d-flex align-items-center px-3 gap-2"
                  style="height: 48px;"
                >
                  <span class="material-symbols-outlined text-outline-variant">calendar_month</span>
                  <input
                    v-model="travelDate"
                    class="bg-transparent border-0 w-100 outline-none font-body text-on-surface text-uppercase"
                    type="date"
                  />
                </div>
              </div>

              <div class="col-12 col-md-6 d-flex flex-column gap-1">
                <label class="small text-uppercase text-on-surface-variant ps-2 fw-bold" style="font-size: 11px;">Travelers</label>
                <div
                  class="neomorph-inset bg-surface rounded-3 d-flex align-items-center px-3 gap-2 cursor-pointer"
                  style="height: 48px;"
                >
                  <span class="material-symbols-outlined text-outline-variant">group</span>
                  <span class="font-body text-on-surface">{{ travelers }}</span>
                </div>
              </div>
            </div>

            <button
              type="submit"
              class="btn border-0 neomorph-btn-primary bg-primary text-on-primary rounded-3 font-headline fs-5 mt-3 d-flex align-items-center justify-center gap-2 py-3 cursor-pointer"
            >
              <span class="material-symbols-outlined">search</span>
              Search Flights
            </button>
          </form>
        </div>

        <div class="w-100 w-md-50 position-relative d-flex align-items-center justify-center" style="min-height: 450px;">
          <div
            class="position-absolute inset-0 bg-surface neomorph-outset overflow-hidden p-3"
            style="border-radius: 40px;"
          >
            <div class="w-100 h-100 overflow-hidden position-relative" style="border-radius: 32px;">
              <img
                class="w-100 h-100 object-fit-cover rounded-4 opacity-75"
                src="https://lh3.googleusercontent.com/aida-public/AB6AXuA7Wxu9z_DnZ4O_6RKNB-DHTGlLl-95FyC-mG5JjKuIhB4xh66jhCF6a4__6AAZ81JCSayIgTxS13RoyuZok6XERjm1qaFY8PuMsEr4E1tVSRtYjnsq56naG3CAJ4OmiYykB4LfZ4jjuuz8dZIaVwUgO7rnVP9dFuEfwu6SGnZM1FwpXstuaroVQ45JUEDlSqJXJg9cqa6xenHxATSNz7UU1mfX98l_uzgn0HePwB-Awb4z-SW3j-g7Pm9z9oGkSAXbWdYt8Q8eWA8"
                alt="Futuristic Terminal"
              />
              <div
                class="position-absolute bottom-0 start-0 end-0 m-4 neomorph-outset bg-surface rounded-3 p-3 d-flex align-items-center justify-content-between backdrop-blur"
              >
                <div>
                  <p class="small text-uppercase text-on-surface-variant mb-0" style="font-size: 11px;">
                    Featured Route
                  </p>
                  <p class="font-headline fs-5 text-on-surface mb-0">
                    JFK
                    <span class="material-symbols-outlined text-primary align-middle mx-1" style="font-size: 16px;"
                      >arrow_forward</span
                    >
                    HND
                  </p>
                </div>
                <div class="text-end">
                  <p class="small text-uppercase text-primary mb-0" style="font-size: 11px;">From</p>
                  <p class="font-headline fs-5 text-on-surface mb-0">$849</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      <!-- Curated Escapes -->
      <section class="w-100 mt-5 d-flex flex-column gap-4">
        <div class="d-flex align-items-end justify-content-between">
          <div>
            <h2 class="font-display fs-2 text-on-background mb-1">
              Curated Escapes
            </h2>
            <p class="font-body fs-6 text-on-surface-variant mb-0">
              Exclusive packages tailored for seamless journeys.
            </p>
          </div>
          <router-link
            to="/search-results"
            class="btn border-0 neomorph-outset bg-surface text-primary px-3 py-2 rounded-pill small d-flex align-items-center gap-2 text-decoration-none"
          >
            View All
            <span class="material-symbols-outlined" style="font-size: 16px;">arrow_forward</span>
          </router-link>
        </div>

        <div class="row g-4">
          <div class="col-12 col-md-4">
            <div
              @click="router.push('/search-results')"
              class="neomorph-outset bg-surface rounded-4 p-3 d-flex flex-column gap-3 cursor-pointer card-hover transition-all"
            >
              <div class="w-100 rounded-3 overflow-hidden position-relative neomorph-inset p-2" style="height: 200px;">
                <img
                  class="w-100 h-100 object-fit-cover rounded-3"
                  src="https://lh3.googleusercontent.com/aida-public/AB6AXuDC_PTCexvm9xmy8y99-dIQ5NCoU6bpsXbTHM0k-6YPHs86fWtOBhNG0AuJdk-5jptUK2WgnHueuiW27MX6B_pzraYCzsh7LQGArEtj7YbRwLsakaEX64Y41HF8fagaMeaAuSsKiyLL8-vAfk1KhBYGiEXo1GPNUbgCUhafw5TBU9F1eIIph8-_GTuL6ZZ0WbhRHYWvhdLe4bFKr5kL9upZG73EczOzrGkD8cSw8mQbgMGkneBhdY9jcBtxdmKLnJZE2yrf-WbOoLs"
                  alt="Maldives"
                />
                <div
                  class="position-absolute top-0 end-0 m-3 neomorph-outset bg-surface px-2 py-1 rounded-pill small text-primary fw-bold"
                >
                  -15%
                </div>
              </div>
              <div class="px-1 pb-1">
                <p class="small text-uppercase text-on-surface-variant mb-1" style="font-size: 11px;">
                  Tropical Retreat
                </p>
                <h3 class="font-headline fs-5 text-on-surface mb-2">
                  Maldives Getaway
                </h3>
                <p class="font-body small text-on-surface-variant mb-3 text-truncate-2">
                  Experience unparalleled luxury in overwater villas with private infinity pools and sunset dining.
                </p>
                <div
                  class="d-flex align-items-center justify-content-between pt-3 border-top"
                >
                  <div class="d-flex flex-column">
                    <span class="small text-on-surface-variant text-decoration-line-through" style="font-size: 12px;"
                      >$3,200</span
                    >
                    <span class="font-headline fs-5 text-primary">$2,720</span>
                  </div>
                  <button
                    class="rounded-circle neomorph-btn-primary bg-primary text-on-primary d-flex align-items-center justify-center border-0"
                    style="width: 40px; height: 40px;"
                  >
                    <span class="material-symbols-outlined" style="font-size: 20px;">arrow_forward</span>
                  </button>
                </div>
              </div>
            </div>
          </div>

          <div class="col-12 col-md-4">
            <div
              @click="router.push('/search-results')"
              class="neomorph-outset bg-surface rounded-4 p-3 d-flex flex-column gap-3 cursor-pointer card-hover transition-all"
            >
              <div class="w-100 rounded-3 overflow-hidden position-relative neomorph-inset p-2" style="height: 200px;">
                <img
                  class="w-100 h-100 object-fit-cover rounded-3"
                  src="https://lh3.googleusercontent.com/aida-public/AB6AXuCmPAsjgqfg8Bcofi1pnQsjjiSUNFXbSiezj36sJoYKnH8TtRmWLYKx8tAa-ED6_wtoIRAe82Zd_QGQzUSxFhbA49kXmGpZQsPF6VA1lH0tersYb88_rnjvxKV14zh-9QS-Gfrv7t_LrmFh6n32Q1WkmII5tPE05dEIOKS4qD4K1r7owFbu84pBmAvNxZK9Wzds504xYh01UnLJJOGI5Z6J3NALrmc_AxdaQD3kSOxCIKjHEZfDvce1sM2p_kZohY-gaEr7NKTdcsg"
                  alt="Tokyo"
                />
              </div>
              <div class="px-1 pb-1">
                <p class="small text-uppercase text-on-surface-variant mb-1" style="font-size: 11px;">
                  Urban Discovery
                </p>
                <h3 class="font-headline fs-5 text-on-surface mb-2">Tokyo Explorer</h3>
                <p class="font-body small text-on-surface-variant mb-3 text-truncate-2">
                  Immerse yourself in the perfect blend of ultra-modern technology and ancient traditions.
                </p>
                <div
                  class="d-flex align-items-center justify-content-between pt-3 border-top"
                >
                  <div class="d-flex flex-column">
                    <span class="small text-on-surface-variant" style="font-size: 12px;">From</span>
                    <span class="font-headline fs-5 text-primary">$1,850</span>
                  </div>
                  <button
                    class="rounded-circle neomorph-btn-primary bg-primary text-on-primary d-flex align-items-center justify-center border-0"
                    style="width: 40px; height: 40px;"
                  >
                    <span class="material-symbols-outlined" style="font-size: 20px;">arrow_forward</span>
                  </button>
                </div>
              </div>
            </div>
          </div>

          <div class="col-12 col-md-4">
            <div
              @click="router.push('/search-results')"
              class="neomorph-outset bg-surface rounded-4 p-3 d-flex flex-column gap-3 cursor-pointer card-hover transition-all"
            >
              <div class="w-100 rounded-3 overflow-hidden position-relative neomorph-inset p-2" style="height: 200px;">
                <img
                  class="w-100 h-100 object-fit-cover rounded-3"
                  src="https://lh3.googleusercontent.com/aida-public/AB6AXuAIo87XstJrjc4qVHpN32alCmijhRQUoRViQLAQ5BJMNqparREoZ0E9qZA3k5brr8ikFouwE5SZf1vr9hZgGF63pUV5taw6bCikfoI9AGWeRZ4R__L2iyrVVtQV-tJVo7dunb1bvX3SVzB6Vx19IRRL_56cgCEbkg3BY1-Dm7l6rRZdwBi-e8AGwALJ4qtq0Bzs1HxVUHuTXdpumKTNs02fAF6keM5jWndjQCdaaBCf5e3_B84rpcuSxQUhl3w8dWbZTVDE6RyKJn0"
                  alt="Swiss Alps"
                />
              </div>
              <div class="px-1 pb-1">
                <p class="small text-uppercase text-on-surface-variant mb-1" style="font-size: 11px;">
                  Alpine Adventure
                </p>
                <h3 class="font-headline fs-5 text-on-surface mb-2">
                  Swiss Alps Summit
                </h3>
                <p class="font-body small text-on-surface-variant mb-3 text-truncate-2">
                  Premium ski passes, luxury chalet accommodation, and breathtaking panoramic mountain views.
                </p>
                <div
                  class="d-flex align-items-center justify-content-between pt-3 border-top"
                >
                  <div class="d-flex flex-column">
                    <span class="small text-on-surface-variant" style="font-size: 12px;">From</span>
                    <span class="font-headline fs-5 text-primary">$2,400</span>
                  </div>
                  <button
                    class="rounded-circle neomorph-btn-primary bg-primary text-on-primary d-flex align-items-center justify-center border-0"
                    style="width: 40px; height: 40px;"
                  >
                    <span class="material-symbols-outlined" style="font-size: 20px;">arrow_forward</span>
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
    </div>
  </main>
</template>

<style scoped>
.hover-primary:hover {
  color: var(--primary) !important;
}
.card-hover:hover {
  transform: translateY(-4px);
}
.text-truncate-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
.backdrop-blur {
  backdrop-filter: blur(8px);
}
</style>
