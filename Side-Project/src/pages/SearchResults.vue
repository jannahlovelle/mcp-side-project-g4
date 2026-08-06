<script setup>
import { ref } from "vue";
import { useRouter, useRoute } from "vue-router";

const router = useRouter();
const route = useRoute();

const fromCity = ref(route.query.from || "New York");
const toCity = ref(route.query.to || "London");

const selectedSort = ref("Recommended");

const selectFlight = (flightId) => {
  router.push({
    path: "/passenger-details",
    query: { flightId },
  });
};
</script>

<template>
  <main class="w-100 pt-5 bg-background pb-5 mt-5">
    <div class="max-w-1400 mx-auto px-3 my-4">
      <!-- Main Results Area -->
      <section class="w-100 d-flex flex-column gap-3">
        <!-- Header / Sort -->
        <div class="d-flex justify-content-between align-items-end mb-2">
          <div>
            <h1 class="font-display display-5 text-on-background mb-0">
              {{ fromCity }}
              <span class="text-outline-variant font-light mx-2">→</span>
              {{ toCity }}
            </h1>
            <p class="font-body text-on-surface-variant small mb-0 mt-1">
              Showing 24 flights for Oct 12, 2026
            </p>
          </div>
          <div class="d-none d-sm-flex align-items-center gap-2">
            <span class="small text-on-surface-variant">Sort by:</span>
            <select
              v-model="selectedSort"
              class="form-select form-select-sm neomorph-inset bg-surface-container rounded-3 border-0 px-3 text-on-surface"
              style="width: 180px"
            >
              <option>Recommended</option>
              <option>Price (Lowest)</option>
              <option>Duration (Shortest)</option>
              <option>Departure (Earliest)</option>
            </select>
          </div>
        </div>

        <!-- Date Carousel -->
        <div class="d-flex gap-2 overflow-x-auto pb-2 no-scrollbar">
          <button
            class="btn border-0 flex-shrink-0 d-flex flex-column align-items-center justify-content-center neomorph-outset rounded-3 bg-surface-container text-on-surface-variant cursor-pointer"
            style="width: 80px; height: 80px"
          >
            <span class="small text-uppercase fw-bold" style="font-size: 11px"
              >OCT 10</span
            >
            <span class="small mt-1">$310</span>
          </button>
          <button
            class="btn border-0 flex-shrink-0 d-flex flex-column align-items-center justify-content-center neomorph-outset rounded-3 bg-surface-container text-on-surface-variant cursor-pointer"
            style="width: 80px; height: 80px"
          >
            <span class="small text-uppercase fw-bold" style="font-size: 11px"
              >OCT 11</span
            >
            <span class="small mt-1">$285</span>
          </button>
          <button
            class="btn border-0 flex-shrink-0 d-flex flex-column align-items-center justify-content-center neomorph-inset rounded-3 bg-surface-container text-primary cursor-pointer"
            style="width: 80px; height: 80px"
          >
            <span class="small text-uppercase fw-bold" style="font-size: 11px"
              >OCT 12</span
            >
            <span class="small mt-1">$240</span>
          </button>
          <button
            class="btn border-0 flex-shrink-0 d-flex flex-column align-items-center justify-content-center neomorph-outset rounded-3 bg-surface-container text-on-surface-variant cursor-pointer"
            style="width: 80px; height: 80px"
          >
            <span class="small text-uppercase fw-bold" style="font-size: 11px"
              >OCT 13</span
            >
            <span class="small mt-1">$300</span>
          </button>
          <button
            class="btn border-0 flex-shrink-0 d-flex flex-column align-items-center justify-content-center neomorph-outset rounded-3 bg-surface-container text-on-surface-variant cursor-pointer"
            style="width: 80px; height: 80px"
          >
            <span class="small text-uppercase fw-bold" style="font-size: 11px"
              >OCT 14</span
            >
            <span class="small mt-1">$350</span>
          </button>
        </div>

        <!-- Flight Cards List -->
        <div class="d-flex flex-column gap-4">
          <!-- Card 1 -->
          <article
            class="neomorph-outset bg-surface-container rounded-4 p-4 d-flex flex-column gap-3 card-hover transition-all"
          >
            <div
              class="d-flex flex-column flex-sm-row justify-content-between align-items-start align-items-sm-center gap-3"
            >
              <div class="d-flex align-items-center gap-3">
                <div
                  class="rounded-circle neomorph-inset d-flex align-items-center justify-content-center bg-surface"
                  style="width: 48px; height: 48px"
                >
                  <span
                    class="material-symbols-outlined text-primary"
                    style="
                      font-size: 28px;
                      font-variation-settings: &quot;FILL&quot; 1;
                    "
                    >flight</span
                  >
                </div>
                <div class="d-flex flex-column">
                  <span class="font-headline fs-6 text-on-surface"
                    >SkyBook Airways</span
                  >
                  <span class="small text-on-surface-variant"
                    >Flight SB-402 · Airbus A350</span
                  >
                </div>
              </div>

              <div
                class="d-flex flex-sm-column align-items-center align-items-sm-end justify-content-between w-100 w-sm-auto gap-2"
              >
                <div class="d-flex flex-column align-items-sm-end">
                  <span class="font-display fs-2 text-primary fw-bold"
                    >$240</span
                  >
                  <span class="small text-on-surface-variant"
                    >One way per traveler</span
                  >
                </div>
                <button
                  @click="selectFlight('SB-402')"
                  class="btn border-0 neomorph-btn-primary bg-primary text-on-primary px-4 py-2 rounded-3 font-headline small text-nowrap cursor-pointer"
                >
                  Select Flight
                </button>
              </div>
            </div>

            <div
              class="border-top border-secondary-subtle opacity-50 my-2"
            ></div>

            <div class="row align-items-center text-center text-sm-start g-3">
              <div class="col-12 col-sm-3 d-flex flex-column">
                <span class="font-headline fs-3 text-on-surface">08:30 AM</span>
                <span class="font-headline fs-6 text-on-surface-variant"
                  >JFK</span
                >
                <span class="small text-on-surface-variant"
                  >New York (Terminal 4)</span
                >
              </div>

              <div
                class="col-12 col-sm-6 d-flex flex-column align-items-center px-3"
              >
                <div class="d-flex justify-content-between w-100 small mb-1">
                  <span
                    class="small text-uppercase text-primary fw-bold"
                    style="font-size: 11px"
                    >7h 15m</span
                  >
                  <span
                    class="small text-uppercase text-on-surface-variant"
                    style="font-size: 11px"
                    >Non-stop</span
                  >
                </div>
                <div
                  class="w-100 neomorph-inset rounded-pill bg-surface-container-high position-relative d-flex align-items-center px-1"
                  style="height: 12px"
                >
                  <div
                    class="position-absolute start-50 translate-middle-x rounded-circle neomorph-outset bg-surface d-flex align-items-center justify-content-center z-1"
                    style="width: 24px; height: 24px"
                  >
                    <span
                      class="material-symbols-outlined text-primary"
                      style="font-size: 16px; transform: rotate(90deg)"
                      >flight</span
                    >
                  </div>
                </div>
              </div>

              <div class="col-12 col-sm-3 d-flex flex-column text-sm-end">
                <span class="font-headline fs-3 text-on-surface">08:45 PM</span>
                <span class="font-headline fs-6 text-on-surface-variant"
                  >LHR</span
                >
                <span class="small text-on-surface-variant"
                  >London Heathrow (T5)</span
                >
              </div>
            </div>

            <div
              class="d-flex justify-content-between align-items-center pt-2 border-top"
            >
              <div class="d-flex align-items-center gap-1">
                <span
                  class="material-symbols-outlined text-secondary"
                  style="font-size: 16px"
                  >airline_seat_recline_extra</span
                >
                <span class="small text-secondary"
                  >4 Seats left at this price</span
                >
              </div>
              <span
                class="badge bg-surface-container-highest text-on-surface-variant rounded px-2 py-1 small"
                >Carry-on included</span
              >
            </div>
          </article>

          <!-- Card 2 -->
          <article
            class="neomorph-outset bg-surface-container rounded-4 p-4 d-flex flex-column gap-3 card-hover transition-all"
          >
            <div
              class="d-flex flex-column flex-sm-row justify-content-between align-items-start align-items-sm-center gap-3"
            >
              <div class="d-flex align-items-center gap-3">
                <div
                  class="rounded-circle neomorph-inset d-flex align-items-center justify-content-center bg-surface"
                  style="width: 48px; height: 48px"
                >
                  <span
                    class="material-symbols-outlined text-tertiary"
                    style="
                      font-size: 28px;
                      font-variation-settings: &quot;FILL&quot; 1;
                    "
                    >flight</span
                  >
                </div>
                <div class="d-flex flex-column">
                  <span class="font-headline fs-6 text-on-surface"
                    >Nimbus Jet</span
                  >
                  <span class="small text-on-surface-variant"
                    >Flight NJ-112 · Boeing 777</span
                  >
                </div>
              </div>

              <div
                class="d-flex flex-sm-column align-items-center align-items-sm-end justify-content-between w-100 w-sm-auto gap-2"
              >
                <div class="d-flex flex-column align-items-sm-end">
                  <span class="font-display fs-2 text-on-surface fw-bold"
                    >$285</span
                  >
                  <span class="small text-on-surface-variant"
                    >One way per traveler</span
                  >
                </div>
                <button
                  @click="selectFlight('NJ-112')"
                  class="btn border-0 neomorph-btn-primary bg-surface text-primary px-4 py-2 rounded-3 font-headline small text-nowrap cursor-pointer"
                >
                  Select Flight
                </button>
              </div>
            </div>

            <div
              class="border-top border-secondary-subtle opacity-50 my-2"
            ></div>

            <div class="row align-items-center text-center text-sm-start g-3">
              <div class="col-12 col-sm-3 d-flex flex-column">
                <span class="font-headline fs-3 text-on-surface">11:00 AM</span>
                <span class="font-headline fs-6 text-on-surface-variant"
                  >JFK</span
                >
                <span class="small text-on-surface-variant"
                  >New York (Terminal 1)</span
                >
              </div>

              <div
                class="col-12 col-sm-6 d-flex flex-column align-items-center px-3"
              >
                <div class="d-flex justify-content-between w-100 small mb-1">
                  <span
                    class="small text-uppercase text-on-surface-variant"
                    style="font-size: 11px"
                    >7h 20m</span
                  >
                  <span
                    class="small text-uppercase text-on-surface-variant"
                    style="font-size: 11px"
                    >Non-stop</span
                  >
                </div>
                <div
                  class="w-100 neomorph-inset rounded-pill bg-surface-container-high position-relative d-flex align-items-center px-1"
                  style="height: 12px"
                >
                  <div
                    class="position-absolute start-50 translate-middle-x rounded-circle neomorph-outset bg-surface d-flex align-items-center justify-content-center z-1"
                    style="width: 24px; height: 24px"
                  >
                    <span
                      class="material-symbols-outlined text-on-surface-variant"
                      style="font-size: 16px; transform: rotate(90deg)"
                      >flight</span
                    >
                  </div>
                </div>
              </div>

              <div class="col-12 col-sm-3 d-flex flex-column text-sm-end">
                <span class="font-headline fs-3 text-on-surface">11:20 PM</span>
                <span class="font-headline fs-6 text-on-surface-variant"
                  >LHR</span
                >
                <span class="small text-on-surface-variant"
                  >London Heathrow (T3)</span
                >
              </div>
            </div>

            <div
              class="d-flex justify-content-between align-items-center pt-2 border-top"
            >
              <div class="d-flex align-items-center gap-1">
                <span
                  class="material-symbols-outlined text-outline"
                  style="font-size: 16px"
                  >airline_seat_recline_normal</span
                >
                <span class="small text-outline"
                  >Plenty of seats available</span
                >
              </div>
              <span
                class="badge bg-surface-container-highest text-on-surface-variant rounded px-2 py-1 small"
                >No carry-on</span
              >
            </div>
          </article>
        </div>
      </section>
    </div>
  </main>
</template>

<style scoped>
.card-hover:hover {
  transform: translateY(-4px);
}
</style>
