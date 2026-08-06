<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'

const router = useRouter()

const firstName = ref('')
const lastName = ref('')
const dob = ref('')
const gender = ref('')
const nationality = ref('us')
const passport = ref('')
const email = ref('')
const phone = ref('')

const isSubmitting = ref(false)

const handleContinue = () => {
  isSubmitting.value = true
  setTimeout(() => {
    isSubmitting.value = false
    router.push('/booking-confirmed')
  }, 1000)
}
</script>

<template>
  <main class="w-100 pt-5 bg-background pb-5 mt-5">
    <div class="max-w-1200 mx-auto px-3 my-4">
      <div class="d-flex flex-column flex-md-row justify-content-between align-items-start align-items-md-end mb-4 gap-2">
        <div class="d-flex flex-column">
          <p class="small text-uppercase text-primary tracking-widest mb-1 font-headline">
            Step 2 of 3
          </p>
          <h1 class="font-display display-5 text-on-background mb-0">
            Passenger Details
          </h1>
        </div>
        <div class="d-flex align-items-center gap-2">
          <div class="rounded-circle neomorph-inset d-flex align-items-center justify-content-center text-primary" style="width: 40px; height: 40px;">
            <span class="material-symbols-outlined" style="font-size: 20px;">person</span>
          </div>
          <div class="rounded-circle neomorph-inset d-flex align-items-center justify-content-center text-outline-variant" style="width: 40px; height: 40px;">
            <span class="material-symbols-outlined" style="font-size: 20px;">luggage</span>
          </div>
          <div class="rounded-circle neomorph-inset d-flex align-items-center justify-content-center text-outline-variant" style="width: 40px; height: 40px;">
            <span class="material-symbols-outlined" style="font-size: 20px;">payment</span>
          </div>
        </div>
      </div>

      <div class="row g-4">
        <div class="col-12 col-lg-8 d-flex flex-column gap-4">
          <div class="neomorph-outset rounded-4 p-4 bg-surface-container-lowest">
            <div class="d-flex align-items-center gap-2 mb-3">
              <span
                class="material-symbols-outlined text-secondary"
                style="font-size: 24px; font-variation-settings: 'FILL' 1"
                >face</span
              >
              <h2 class="font-headline fs-5 text-on-surface mb-0">
                Adult 1 (Primary Contact)
              </h2>
            </div>

            <form @submit.prevent="handleContinue" id="passenger-form">
              <div class="row g-3 mb-3">
                <div class="col-12 col-md-6 d-flex flex-column gap-1">
                  <label class="small text-on-surface-variant ps-2">First Name (as on ID)</label>
                  <input
                    v-model="firstName"
                    class="form-control border-0 neomorph-inset bg-surface-container-lowest rounded-3 py-2 px-3 font-body text-on-surface"
                    placeholder="e.g. Jane"
                    required
                    type="text"
                  />
                </div>
                <div class="col-12 col-md-6 d-flex flex-column gap-1">
                  <label class="small text-on-surface-variant ps-2">Last Name</label>
                  <input
                    v-model="lastName"
                    class="form-control border-0 neomorph-inset bg-surface-container-lowest rounded-3 py-2 px-3 font-body text-on-surface"
                    placeholder="e.g. Doe"
                    required
                    type="text"
                  />
                </div>
              </div>

              <div class="row g-3 mb-3">
                <div class="col-12 col-md-4 d-flex flex-column gap-1">
                  <label class="small text-on-surface-variant ps-2">Date of Birth</label>
                  <input
                    v-model="dob"
                    class="form-control border-0 neomorph-inset bg-surface-container-lowest rounded-3 py-2 px-3 font-body text-on-surface"
                    required
                    type="date"
                  />
                </div>
                <div class="col-12 col-md-4 d-flex flex-column gap-1">
                  <label class="small text-on-surface-variant ps-2">Gender</label>
                  <select
                    v-model="gender"
                    class="form-select border-0 neomorph-inset bg-surface-container-lowest rounded-3 py-2 px-3 font-body text-on-surface"
                    required
                  >
                    <option disabled value="">Select</option>
                    <option value="f">Female</option>
                    <option value="m">Male</option>
                    <option value="u">Unspecified</option>
                  </select>
                </div>
                <div class="col-12 col-md-4 d-flex flex-column gap-1">
                  <label class="small text-on-surface-variant ps-2">Nationality</label>
                  <select
                    v-model="nationality"
                    class="form-select border-0 neomorph-inset bg-surface-container-lowest rounded-3 py-2 px-3 font-body text-on-surface"
                    required
                  >
                    <option disabled value="">Select</option>
                    <option value="us">United States</option>
                    <option value="uk">United Kingdom</option>
                    <option value="ca">Canada</option>
                    <option value="au">Australia</option>
                  </select>
                </div>
              </div>

              <div class="border-top my-3 opacity-25"></div>

              <div class="row g-3">
                <div class="col-12 col-md-6 d-flex flex-column gap-1">
                  <label class="small text-on-surface-variant ps-2">Passport Number</label>
                  <input
                    v-model="passport"
                    class="form-control border-0 neomorph-inset bg-surface-container-lowest rounded-3 py-2 px-3 font-body text-on-surface text-uppercase"
                    placeholder="Optional for domestic"
                    type="text"
                  />
                </div>
              </div>
            </form>
          </div>

          <div class="neomorph-outset rounded-4 p-4 bg-surface-container-lowest">
            <div class="d-flex align-items-center gap-2 mb-3">
              <span
                class="material-symbols-outlined text-secondary"
                style="font-size: 24px; font-variation-settings: 'FILL' 1"
                >contact_mail</span
              >
              <h2 class="font-headline fs-5 text-on-surface mb-0">
                Contact Information
              </h2>
            </div>
            <div class="row g-3">
              <div class="col-12 col-md-6 d-flex flex-column gap-1">
                <label class="small text-on-surface-variant ps-2">Email Address</label>
                <input
                  v-model="email"
                  class="form-control border-0 neomorph-inset bg-surface-container-lowest rounded-3 py-2 px-3 font-body text-on-surface"
                  form="passenger-form"
                  placeholder="Confirmation will be sent here"
                  required
                  type="email"
                />
              </div>
              <div class="col-12 col-md-6 d-flex flex-column gap-1">
                <label class="small text-on-surface-variant ps-2">Phone Number</label>
                <div class="input-group">
                  <span class="input-group-text border-0 neomorph-inset bg-surface-container-lowest rounded-start-3 text-on-surface px-3" style="width: 60px;">+1</span>
                  <input
                    v-model="phone"
                    class="form-control border-0 neomorph-inset bg-surface-container-lowest rounded-end-3 py-2 px-3 font-body text-on-surface"
                    form="passenger-form"
                    placeholder="(555) 000-0000"
                    required
                    type="tel"
                  />
                </div>
              </div>
            </div>
          </div>

          <div class="d-flex justify-content-between align-items-center mt-2">
            <button
              @click="router.push('/search-results')"
              class="btn border-0 neomorph-btn-primary bg-surface-container-lowest text-on-surface-variant px-4 py-2 rounded-3 font-headline d-flex align-items-center gap-2 cursor-pointer"
              type="button"
            >
              <span class="material-symbols-outlined" style="font-size: 20px;">arrow_back</span>
              Back
            </button>
            <button
              :disabled="isSubmitting"
              class="btn border-0 neomorph-btn-primary bg-primary text-on-primary px-4 py-2 rounded-3 font-headline d-flex align-items-center gap-2 cursor-pointer"
              form="passenger-form"
              type="submit"
            >
              <span v-if="isSubmitting" class="d-flex align-items-center gap-2">
                <span class="spinner-border spinner-border-sm"></span>
                Processing...
              </span>
              <span v-else class="d-flex align-items-center gap-2">
                Continue to Payment
                <span class="material-symbols-outlined" style="font-size: 20px;">arrow_forward</span>
              </span>
            </button>
          </div>
        </div>

        <aside class="col-12 col-lg-4">
          <div class="neomorph-outset rounded-4 p-4 bg-surface-container-lowest sticky-top" style="top: 100px;">
            <div class="d-flex align-items-center justify-content-between mb-3">
              <h3 class="font-headline fs-5 text-on-surface mb-0">
                Flight Summary
              </h3>
              <span class="badge bg-primary-container text-on-primary-container rounded-pill px-3 py-1"
                >OUTBOUND</span
              >
            </div>
            <div class="d-flex flex-column gap-1 mb-3 text-center">
              <div class="d-flex justify-content-between align-items-center px-2">
                <span class="font-headline fs-3 text-primary">JFK</span>
                <div class="flex-grow-1 mx-3 position-relative d-flex align-items-center justify-content-center">
                  <div class="w-100 border-top border-primary opacity-25"></div>
                  <span class="material-symbols-outlined position-absolute text-secondary bg-surface-container-lowest px-1" style="font-size: 20px; transform: rotate(90deg);"
                    >flight</span
                  >
                </div>
                <span class="font-headline fs-3 text-primary">LHR</span>
              </div>
              <p class="small text-on-surface-variant mb-0">
                Fri, Oct 24 • Non-stop • 7h 15m
              </p>
            </div>
            <div class="border-top my-3 opacity-25"></div>
            <div class="d-flex flex-column gap-2">
              <div class="d-flex justify-content-between align-items-end">
                <span class="small text-on-surface-variant">1x Adult Ticket</span>
                <span class="font-headline text-on-surface">$845.00</span>
              </div>
              <div class="d-flex justify-content-between align-items-end">
                <span class="small text-on-surface-variant">Taxes & Fees</span>
                <span class="font-headline small text-on-surface">$112.40</span>
              </div>
            </div>
            <div class="border-top my-3 opacity-25"></div>
            <div class="d-flex justify-content-between align-items-end">
              <span class="font-headline fs-5 text-on-surface">Total</span>
              <span class="font-display fs-3 text-primary">$957.40</span>
            </div>
          </div>
        </aside>
      </div>
    </div>
  </main>
</template>
