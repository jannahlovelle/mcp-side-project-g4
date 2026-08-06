<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const flightNumber = ref('')
const aircraftType = ref('')
const originCity = ref('')
const destinationCity = ref('')
const departureTime = ref('')
const arrivalTime = ref('')
const baseFare = ref('')
const totalSeats = ref('')

const handleSubmit = () => {
  router.push('/manage-flights')
}
</script>

<template>
  <main class="w-100 pt-5 bg-background pb-5 mt-5">
    <div class="max-w-1200 mx-auto px-3 my-4 d-flex flex-column gap-4">
      <div class="position-relative">
        <h1 class="font-display display-5 text-primary mb-2">Add New Flight</h1>
        <p class="font-body fs-6 text-on-surface-variant mb-0" style="max-width: 650px;">
          Enter the details below to schedule a new flight in the SkyBook system. Ensure all fields are completed accurately before submission.
        </p>
      </div>

      <form @submit.prevent="handleSubmit" class="w-100 d-flex flex-column gap-4 bg-surface-container-lowest neomorph-outset rounded-4 p-4 p-md-5">
        <div class="row g-4">
          <div class="col-12 col-md-6 d-flex flex-column gap-1">
            <label class="small text-uppercase text-on-surface-variant ps-2 fw-bold" style="font-size: 11px;" for="flightNumber">Flight Number</label>
            <input
              v-model="flightNumber"
              id="flightNumber"
              class="form-control border-0 neomorph-inset bg-surface-container-lowest rounded-3 py-2 px-3 font-body text-on-surface"
              placeholder="e.g., SB-101"
              required
              type="text"
            />
          </div>

          <div class="col-12 col-md-6 d-flex flex-column gap-1">
            <label class="small text-uppercase text-on-surface-variant ps-2 fw-bold" style="font-size: 11px;" for="aircraftType">Aircraft Type</label>
            <select
              v-model="aircraftType"
              id="aircraftType"
              class="form-select border-0 neomorph-inset bg-surface-container-lowest rounded-3 py-2 px-3 font-body text-on-surface cursor-pointer"
              required
            >
              <option disabled value="">Select Aircraft</option>
              <option value="boeing-737">Boeing 737</option>
              <option value="airbus-a320">Airbus A320</option>
              <option value="boeing-777">Boeing 777</option>
              <option value="airbus-a350">Airbus A350</option>
            </select>
          </div>

          <div class="col-12 border-top opacity-25 my-1"></div>

          <div class="col-12 col-md-6 d-flex flex-column gap-1">
            <label class="small text-uppercase text-on-surface-variant ps-2 fw-bold" style="font-size: 11px;" for="originCity">Origin City</label>
            <div class="input-group">
              <span class="input-group-text border-0 neomorph-inset bg-surface-container-lowest rounded-start-3 text-primary px-3">
                <span class="material-symbols-outlined" style="font-size: 20px;">flight_takeoff</span>
              </span>
              <input
                v-model="originCity"
                id="originCity"
                class="form-control border-0 neomorph-inset bg-surface-container-lowest rounded-end-3 py-2 px-3 font-body text-on-surface"
                placeholder="e.g., New York, USA"
                required
                type="text"
              />
            </div>
          </div>

          <div class="col-12 col-md-6 d-flex flex-column gap-1">
            <label class="small text-uppercase text-on-surface-variant ps-2 fw-bold" style="font-size: 11px;" for="destinationCity">Destination City</label>
            <div class="input-group">
              <span class="input-group-text border-0 neomorph-inset bg-surface-container-lowest rounded-start-3 text-primary px-3">
                <span class="material-symbols-outlined" style="font-size: 20px;">flight_land</span>
              </span>
              <input
                v-model="destinationCity"
                id="destinationCity"
                class="form-control border-0 neomorph-inset bg-surface-container-lowest rounded-end-3 py-2 px-3 font-body text-on-surface"
                placeholder="e.g., London, UK"
                required
                type="text"
              />
            </div>
          </div>

          <div class="col-12 border-top opacity-25 my-1"></div>

          <div class="col-12 col-md-6 d-flex flex-column gap-1">
            <label class="small text-uppercase text-on-surface-variant ps-2 fw-bold" style="font-size: 11px;" for="departureTime">Departure Date & Time</label>
            <input
              v-model="departureTime"
              id="departureTime"
              class="form-control border-0 neomorph-inset bg-surface-container-lowest rounded-3 py-2 px-3 font-body text-on-surface"
              required
              type="datetime-local"
            />
          </div>

          <div class="col-12 col-md-6 d-flex flex-column gap-1">
            <label class="small text-uppercase text-on-surface-variant ps-2 fw-bold" style="font-size: 11px;" for="arrivalTime">Arrival Date & Time</label>
            <input
              v-model="arrivalTime"
              id="arrivalTime"
              class="form-control border-0 neomorph-inset bg-surface-container-lowest rounded-3 py-2 px-3 font-body text-on-surface"
              required
              type="datetime-local"
            />
          </div>

          <div class="col-12 border-top opacity-25 my-1"></div>

          <div class="col-12 col-md-6 d-flex flex-column gap-1">
            <label class="small text-uppercase text-on-surface-variant ps-2 fw-bold" style="font-size: 11px;" for="baseFare">Base Fare (USD)</label>
            <div class="input-group">
              <span class="input-group-text border-0 neomorph-inset bg-surface-container-lowest rounded-start-3 text-on-surface-variant px-3">$</span>
              <input
                v-model="baseFare"
                id="baseFare"
                class="form-control border-0 neomorph-inset bg-surface-container-lowest rounded-end-3 py-2 px-3 font-body text-on-surface"
                min="0"
                placeholder="0.00"
                required
                step="0.01"
                type="number"
              />
            </div>
          </div>

          <div class="col-12 col-md-6 d-flex flex-column gap-1">
            <label class="small text-uppercase text-on-surface-variant ps-2 fw-bold" style="font-size: 11px;" for="totalSeats">Total Seats</label>
            <div class="input-group">
              <span class="input-group-text border-0 neomorph-inset bg-surface-container-lowest rounded-start-3 text-on-surface-variant px-3">
                <span class="material-symbols-outlined" style="font-size: 20px;">event_seat</span>
              </span>
              <input
                v-model="totalSeats"
                id="totalSeats"
                class="form-control border-0 neomorph-inset bg-surface-container-lowest rounded-end-3 py-2 px-3 font-body text-on-surface"
                min="1"
                placeholder="e.g., 180"
                required
                type="number"
              />
            </div>
          </div>
        </div>

        <div class="d-flex align-items-center justify-content-end gap-3 mt-3 pt-3 border-top">
          <button
            @click="router.push('/manage-flights')"
            class="btn border-0 neomorph-outset px-4 py-2 rounded-3 font-headline text-on-surface-variant cursor-pointer"
            type="button"
          >
            Cancel
          </button>
          <button
            class="btn border-0 bg-primary text-on-primary neomorph-btn-primary px-4 py-2 rounded-3 font-headline d-flex align-items-center gap-2 cursor-pointer"
            type="submit"
          >
            <span class="material-symbols-outlined" style="font-size: 20px;">add_circle</span>
            Create Flight
          </button>
        </div>
      </form>
    </div>
  </main>
</template>
