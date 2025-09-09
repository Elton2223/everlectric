<template>
  <section id="pricing" class="py-20 relative">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
          Calculate Your Savings
        </h2>
        <p class="text-xl text-gray-300 max-w-3xl mx-auto">
          See how much you can save by switching to electric vehicles with our cost calculator.
        </p>
      </div>
      
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
        <!-- Calculator Form -->
        <div class="glass-strong rounded-3xl p-8">
          <h3 class="text-2xl font-bold text-white mb-8">Fleet Information</h3>
          
          <form class="space-y-6">
            <div>
              <label class="block text-sm font-medium text-gray-300 mb-2">Number of Vehicles</label>
              <input
                v-model.number="calculator.vehicleCount"
                type="number"
                min="1"
                max="1000"
                class="w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400"
                placeholder="Enter number of vehicles"
              />
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-300 mb-2">Average Monthly Distance per Vehicle (km)</label>
              <input
                v-model.number="calculator.monthlyDistance"
                type="number"
                min="100"
                max="10000"
                class="w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400"
                placeholder="Enter monthly distance"
              />
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-300 mb-2">Current Fuel Cost per Liter (R)</label>
              <input
                v-model.number="calculator.fuelCost"
                type="number"
                step="0.01"
                min="10"
                max="50"
                class="w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400"
                placeholder="Enter current fuel cost"
              />
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-300 mb-2">Average Fuel Consumption (L/100km)</label>
              <input
                v-model.number="calculator.fuelConsumption"
                type="number"
                step="0.1"
                min="5"
                max="30"
                class="w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400"
                placeholder="Enter fuel consumption"
              />
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-300 mb-2">Monthly Maintenance Cost per Vehicle (R)</label>
              <input
                v-model.number="calculator.maintenanceCost"
                type="number"
                min="0"
                max="10000"
                class="w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400"
                placeholder="Enter maintenance cost"
              />
            </div>
          </form>
        </div>
        
        <!-- Results -->
        <div class="space-y-6">
          <!-- Current Costs -->
          <div class="glass-card rounded-2xl p-6">
            <h4 class="text-xl font-semibold text-white mb-4">Current Monthly Costs</h4>
            <div class="space-y-3">
              <div class="flex justify-between">
                <span class="text-gray-300">Fuel Costs:</span>
                <span class="text-white font-semibold">R{{ currentFuelCosts.toLocaleString() }}</span>
              </div>
              <div class="flex justify-between">
                <span class="text-gray-300">Maintenance:</span>
                <span class="text-white font-semibold">R{{ currentMaintenanceCosts.toLocaleString() }}</span>
              </div>
              <div class="flex justify-between border-t border-white/10 pt-3">
                <span class="text-gray-300 font-semibold">Total Monthly:</span>
                <span class="text-white font-bold text-lg">R{{ currentTotalCosts.toLocaleString() }}</span>
              </div>
            </div>
          </div>
          
          <!-- Electric Vehicle Costs -->
          <div class="glass-card rounded-2xl p-6">
            <h4 class="text-xl font-semibold text-white mb-4">With Everlectric EVaaS</h4>
            <div class="space-y-3">
              <div class="flex justify-between">
                <span class="text-gray-300">Monthly Package:</span>
                <span class="text-electric-400 font-semibold">R{{ evCosts.toLocaleString() }}</span>
              </div>
              <div class="flex justify-between">
                <span class="text-gray-300">Maintenance:</span>
                <span class="text-electric-400 font-semibold">R0</span>
              </div>
              <div class="flex justify-between">
                <span class="text-gray-300">Fuel:</span>
                <span class="text-electric-400 font-semibold">R0</span>
              </div>
              <div class="flex justify-between border-t border-white/10 pt-3">
                <span class="text-gray-300 font-semibold">Total Monthly:</span>
                <span class="text-electric-400 font-bold text-lg">R{{ evCosts.toLocaleString() }}</span>
              </div>
            </div>
          </div>
          
          <!-- Savings -->
          <div class="glass-strong rounded-2xl p-6 text-center">
            <h4 class="text-xl font-semibold text-white mb-4">Your Monthly Savings</h4>
            <div class="text-4xl font-bold text-electric-400 mb-2">
              R{{ monthlySavings.toLocaleString() }}
            </div>
            <div class="text-gray-300 mb-4">
              {{ savingsPercentage }}% reduction in costs
            </div>
            <div class="text-sm text-gray-400">
              Annual savings: R{{ annualSavings.toLocaleString() }}
            </div>
          </div>
          
          <!-- CTA -->
          <div class="text-center">
            <button 
              @click="scrollToContact"
              class="glass-strong px-8 py-4 rounded-lg text-white font-semibold text-lg hover:bg-white/20 transition-all duration-300 electric-glow"
            >
              Get Your Custom Quote
            </button>
          </div>
        </div>
      </div>
      
      <!-- Additional Benefits -->
      <div class="mt-16 glass-strong rounded-3xl p-8 md:p-12">
        <h3 class="text-3xl font-bold text-white text-center mb-12">
          Additional Benefits Not Included in Cost Calculation
        </h3>
        
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div class="text-center">
            <div class="w-16 h-16 glass-strong rounded-2xl flex items-center justify-center mx-auto mb-4">
              <svg class="w-8 h-8 text-electric-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 12l2 2 4-4m6 2a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
            </div>
            <h4 class="text-lg font-semibold text-white mb-2">Zero Technology Risk</h4>
            <p class="text-gray-300 text-sm">Always have access to the latest EV technology without ownership risk</p>
          </div>
          
          <div class="text-center">
            <div class="w-16 h-16 glass-strong rounded-2xl flex items-center justify-center mx-auto mb-4">
              <svg class="w-8 h-8 text-electric-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z" />
              </svg>
            </div>
            <h4 class="text-lg font-semibold text-white mb-2">Instant Scalability</h4>
            <p class="text-gray-300 text-sm">Add or reduce vehicles based on your business needs</p>
          </div>
          
          <div class="text-center">
            <div class="w-16 h-16 glass-strong rounded-2xl flex items-center justify-center mx-auto mb-4">
              <svg class="w-8 h-8 text-electric-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
              </svg>
            </div>
            <h4 class="text-lg font-semibold text-white mb-2">Environmental Impact</h4>
            <p class="text-gray-300 text-sm">Reduce your carbon footprint and meet sustainability goals</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const calculator = ref({
  vehicleCount: 10,
  monthlyDistance: 2000,
  fuelCost: 22.50,
  fuelConsumption: 8.5,
  maintenanceCost: 1500
})

// EVaaS pricing per vehicle per month (example pricing)
const EV_COST_PER_VEHICLE = 8500

const currentFuelCosts = computed(() => {
  const totalDistance = calculator.value.vehicleCount * calculator.value.monthlyDistance
  const totalFuel = (totalDistance / 100) * calculator.value.fuelConsumption
  return Math.round(totalFuel * calculator.value.fuelCost)
})

const currentMaintenanceCosts = computed(() => {
  return calculator.value.vehicleCount * calculator.value.maintenanceCost
})

const currentTotalCosts = computed(() => {
  return currentFuelCosts.value + currentMaintenanceCosts.value
})

const evCosts = computed(() => {
  return calculator.value.vehicleCount * EV_COST_PER_VEHICLE
})

const monthlySavings = computed(() => {
  return Math.max(0, currentTotalCosts.value - evCosts.value)
})

const annualSavings = computed(() => {
  return monthlySavings.value * 12
})

const savingsPercentage = computed(() => {
  if (currentTotalCosts.value === 0) return 0
  return Math.round((monthlySavings.value / currentTotalCosts.value) * 100)
})

const scrollToContact = () => {
  const element = document.querySelector('#contact')
  if (element) {
    element.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    })
  }
}
</script>
