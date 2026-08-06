<script setup>
import { ref, computed } from "vue";
import { useRouter } from "vue-router";

const router = useRouter();

const searchQuery = ref("");
const flights = ref([
  {
    code: "SB-402",
    aircraft: "Boeing 787",
    originCode: "JFK",
    originCity: "New York",
    destCode: "LHR",
    destCity: "London",
    schedule: "Oct 24, 08:30 AM",
    duration: "7h 15m",
    fare: 450,
    bookedSeats: 180,
    totalSeats: 220,
    progress: 82,
    color: "primary",
  },
  {
    code: "SB-115",
    aircraft: "Airbus A320",
    originCode: "SFO",
    originCity: "San Francisco",
    destCode: "ORD",
    destCity: "Chicago",
    schedule: "Oct 25, 11:15 AM",
    duration: "4h 20m",
    fare: 280,
    bookedSeats: 45,
    totalSeats: 150,
    progress: 30,
    color: "tertiary",
  },
  {
    code: "SB-808",
    aircraft: "Boeing 777X",
    originCode: "LAX",
    originCity: "Los Angeles",
    destCode: "HND",
    destCity: "Tokyo",
    schedule: "Oct 26, 01:45 PM",
    duration: "11h 30m",
    fare: 890,
    bookedSeats: 290,
    totalSeats: 300,
    progress: 96,
    color: "secondary",
  },
]);

const filteredFlights = computed(() => {
  if (!searchQuery.value.trim()) return flights.value;
  const q = searchQuery.value.toLowerCase();
  return flights.value.filter(
    (f) =>
      f.code.toLowerCase().includes(q) ||
      f.originCity.toLowerCase().includes(q) ||
      f.destCity.toLowerCase().includes(q) ||
      f.originCode.toLowerCase().includes(q) ||
      f.destCode.toLowerCase().includes(q),
  );
});

const deleteFlight = (index) => {
  flights.value.splice(index, 1);
};
</script>

<template>
  <main class="w-100 pt-5 bg-background pb-5 mt-5">
    <div
      class="max-w-1400 mx-auto px-3 my-4 d-flex flex-column gap-4 position-relative"
    >
      <!-- Header Section -->
      <div
        class="d-flex flex-column flex-md-row justify-content-between align-items-start align-items-md-end w-100 gap-3 z-1"
      >
        <div class="d-flex flex-column gap-1" style="max-width: 600px">
          <h1 class="font-display display-5 text-primary mb-0 tracking-tight">
            Flight Manifest
          </h1>
          <p class="font-body fs-6 text-on-surface-variant mb-0">
            Manage active routes, monitor seat availability, and update flight
            details across the network.
          </p>
        </div>
        <div class="d-flex align-items-center gap-2">
          <button
            @click="router.push('/add-flight')"
            class="btn border-0 neomorph-btn-primary bg-primary text-on-primary px-4 py-2 rounded-3 font-headline small d-flex align-items-center gap-2 cursor-pointer"
          >
            <span class="material-symbols-outlined" style="font-size: 18px"
              >add</span
            >
            Add New Flight
          </button>
        </div>
      </div>

      <!-- Background Glow -->
      <div
        class="position-absolute top-0 end-0 rounded-circle blur-3"
        style="
          width: 400px;
          height: 400px;
          background: rgba(116, 209, 255, 0.15);
          pointer-events: none;
        "
      ></div>

      <div
        class="w-100 d-flex flex-column gap-3 neomorph-outset bg-surface p-4 rounded-4"
      >
        <!-- Filters / Search Bar -->
        <div
          class="d-flex align-items-center justify-content-between w-100 pb-3 border-bottom position-relative"
        >
          <div
            class="d-flex align-items-center gap-2 flex-grow-1"
            style="max-width: 400px"
          >
            <div
              class="position-relative w-100 neomorph-inset rounded-pill d-flex align-items-center bg-surface px-3"
              style="height: 42px"
            >
              <span
                class="material-symbols-outlined text-outline me-2"
                style="font-size: 20px"
                >search</span
              >
              <input
                v-model="searchQuery"
                class="w-100 bg-transparent border-0 outline-none font-body small text-on-surface"
                placeholder="Search by flight # or city..."
                type="text"
              />
            </div>
          </div>
          <div class="d-flex align-items-center gap-2">
            <button
              class="btn border-0 neomorph-outset px-3 py-2 rounded-pill small font-headline text-primary d-flex align-items-center gap-1"
            >
              <span class="material-symbols-outlined" style="font-size: 16px"
                >filter_list</span
              >
              Filter
            </button>
            <button
              class="btn border-0 neomorph-outset px-3 py-2 rounded-pill small font-headline text-on-surface d-flex align-items-center gap-1"
            >
              <span class="material-symbols-outlined" style="font-size: 16px"
                >sort</span
              >
              Sort
            </button>
          </div>
        </div>

        <!-- Table Header (Desktop) -->

        <!-- Data Rows -->
        <div class="d-flex flex-column gap-2 w-100">
          <div
            v-for="(flight, index) in filteredFlights"
            :key="flight.code"
            class="row g-3 align-items-center p-3 neomorph-outset rounded-3 bg-surface transition-all card-hover"
          >
            <div class="col-12 col-md-2 d-flex align-items-center gap-2">
              <div
                class="rounded-circle neomorph-inset d-flex align-items-center justify-content-center bg-surface"
                style="width: 40px; height: 40px"
              >
                <span
                  class="material-symbols-outlined text-primary"
                  style="font-size: 20px"
                  >flight_takeoff</span
                >
              </div>
              <div class="d-flex flex-column">
                <span class="font-headline fs-6 text-on-surface">{{
                  flight.code
                }}</span>
                <span
                  class="small text-outline text-uppercase"
                  style="font-size: 11px"
                  >{{ flight.aircraft }}</span
                >
              </div>
            </div>

            <div class="col-12 col-md-3 d-flex align-items-center gap-3">
              <div class="d-flex flex-column">
                <span class="font-headline fs-6 text-on-surface">{{
                  flight.originCode
                }}</span>
                <span class="small text-outline" style="font-size: 11px">{{
                  flight.originCity
                }}</span>
              </div>

              <!-- Track line with floating plane icon -->
              <div
                class="flex-grow-1 position-relative neomorph-inset rounded-pill bg-surface d-flex align-items-center px-1"
                style="height: 6px; max-width: 90px"
              >
                <div
                  class="position-absolute start-0 top-50 translate-middle-y rounded-pill bg-primary"
                  :style="{ width: flight.progress + '%', height: '3px' }"
                ></div>
                <span
                  class="material-symbols-outlined position-absolute start-50 top-50 translate-middle text-primary bg-surface rounded-circle neomorph-outset p-1"
                  style="
                    font-size: 14px;
                    transform: translate(-50%, -50%) rotate(90deg);
                  "
                  >flight</span
                >
              </div>

              <div class="d-flex flex-column text-end">
                <span class="font-headline fs-6 text-on-surface">{{
                  flight.destCode
                }}</span>
                <span class="small text-outline" style="font-size: 11px">{{
                  flight.destCity
                }}</span>
              </div>
            </div>

            <div class="col-12 col-md-3 d-flex flex-column">
              <span class="font-body small text-on-surface">{{
                flight.schedule
              }}</span>
              <span class="small text-outline" style="font-size: 11px"
                >Duration: {{ flight.duration }}</span
              >
            </div>

            <div
              class="col-12 col-md-1 d-flex flex-md-column justify-content-between justify-content-md-center align-items-md-end text-end"
            >
              <span class="d-md-none small text-outline" style="font-size: 10px"
                >Fare</span
              >
              <span class="font-headline fs-6 text-primary"
                >${{ flight.fare }}</span
              >
            </div>

            <div
              class="col-12 col-md-2 d-flex flex-column gap-1 align-items-center justify-content-center"
            >
              <div
                class="d-flex justify-content-between w-100"
                style="max-width: 100px; font-size: 10px"
              >
                <span class="text-outline"
                  >{{ flight.bookedSeats }}/{{ flight.totalSeats }}</span
                >
                <span class="text-primary fw-bold">{{ flight.progress }}%</span>
              </div>
              <div
                class="progress w-100 neomorph-inset rounded-pill bg-surface"
                style="height: 8px; max-width: 100px"
              >
                <div
                  class="progress-bar bg-primary rounded-pill transition-all"
                  :style="{ width: flight.progress + '%' }"
                ></div>
              </div>
            </div>

            <div class="col-12 col-md-1 d-flex justify-content-end gap-2">
              <button
                @click="router.push('/add-flight')"
                class="btn border-0 rounded-circle neomorph-btn-primary d-flex align-items-center justify-content-center text-secondary bg-surface p-0 cursor-pointer"
                style="width: 32px; height: 32px"
                title="Edit"
              >
                <span class="material-symbols-outlined" style="font-size: 16px"
                  >edit</span
                >
              </button>
              <button
                @click="deleteFlight(index)"
                class="btn border-0 rounded-circle neomorph-btn-primary d-flex align-items-center justify-content-center text-danger bg-surface p-0 cursor-pointer"
                style="width: 32px; height: 32px"
                title="Delete"
              >
                <span class="material-symbols-outlined" style="font-size: 16px"
                  >delete</span
                >
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.tracking-tight {
  letter-spacing: -0.02em;
}
.card-hover:hover {
  background-color: var(--surface-container-low) !important;
}
</style>
