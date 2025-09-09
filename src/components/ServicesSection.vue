<template>
  <section id="services" class="py-20 relative">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
          Electric Vehicles as a Service
        </h2>
        <p class="text-xl text-gray-300 max-w-3xl mx-auto">
          An everlasting impact on your business with zero upfront costs and maximum efficiency.
        </p>
      </div>
      
      <!-- Services Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div 
          v-for="(service, index) in services" 
          :key="index"
          class="glass-card rounded-2xl p-8 text-center group hover:scale-105 transition-all duration-300"
          :style="{ animationDelay: `${index * 0.1}s` }"
        >
          <!-- Icon -->
          <div class="w-16 h-16 mx-auto mb-6 glass-strong rounded-2xl flex items-center justify-center group-hover:animate-glow">
            <component :is="service.icon" class="w-8 h-8 text-electric-400" />
          </div>
          
          <!-- Title -->
          <h3 class="text-xl font-semibold text-white mb-4">
            {{ service.title }}
          </h3>
          
          <!-- Description -->
          <p class="text-gray-300 leading-relaxed">
            {{ service.description }}
          </p>
        </div>
      </div>
      
      <!-- Fuel Promise Section -->
      <div class="mt-20 glass-strong rounded-3xl p-8 md:p-12 text-center">
        <h3 class="text-3xl md:text-4xl font-bold text-white mb-6">
          "Never pay for fuel again."
        </h3>
        <p class="text-lg md:text-xl text-gray-300 mb-8 max-w-4xl mx-auto">
          Everlectric's packaged solution includes all the electricity (fuel) you need, easily accessed via the Everlectric EV Fast Charger Network wherever you need it most.
        </p>
        
        <!-- Charging Network Visual -->
        <div class="relative max-w-4xl mx-auto">
          <div class="glass-card rounded-2xl p-8">
            <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
              <div v-for="i in 8" :key="i" class="aspect-square glass rounded-xl flex items-center justify-center">
                <div class="w-8 h-8 bg-electric-400 rounded-full animate-pulse"></div>
              </div>
            </div>
            <p class="text-sm text-gray-400 mt-4">Distributed Charging Network</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { 
  CurrencyDollarIcon, 
  BoltIcon, 
  WrenchScrewdriverIcon, 
  ShieldCheckIcon, 
  CogIcon, 
  ChartBarIcon 
} from '@heroicons/vue/24/outline'

const services = [
  {
    icon: CurrencyDollarIcon,
    title: "No upfront Electric Vehicle Investment",
    description: "Start your electric journey with zero initial capital investment. We handle all the upfront costs."
  },
  {
    icon: BoltIcon,
    title: "All Electrical Fuel Included",
    description: "Never worry about fuel costs again. All your electricity needs are included in your monthly package."
  },
  {
    icon: WrenchScrewdriverIcon,
    title: "No upfront Charger Investment",
    description: "Access our comprehensive charging network without any infrastructure investment on your part."
  },
  {
    icon: ShieldCheckIcon,
    title: "No Technology Risk",
    description: "Stay ahead with the latest EV technology without the risk of outdated equipment."
  },
  {
    icon: CogIcon,
    title: "No Maintenance Costs",
    description: "All maintenance and servicing is included in your package. Focus on your business, not vehicle upkeep."
  },
  {
    icon: ChartBarIcon,
    title: "No Fuel Price Fluctuations",
    description: "Lock in predictable operational costs with our fixed-rate electricity packages."
  }
]
</script>
