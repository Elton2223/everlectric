<template>
  <section id="features" class="py-20 relative">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
          Operational Excellence
        </h2>
        <p class="text-xl text-gray-300 max-w-3xl mx-auto">
          We guarantee your operational costs for the next 5 years, providing predictable and sustainable fleet management.
        </p>
      </div>
      
      <!-- Features Grid -->
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12 items-center">
        <!-- Left Column - Features List -->
        <div class="space-y-8">
          <div 
            v-for="(feature, index) in features" 
            :key="index"
            class="glass-card rounded-2xl p-6 flex items-start space-x-4 group hover:scale-105 transition-all duration-300"
            :style="{ animationDelay: `${index * 0.1}s` }"
          >
            <!-- Icon -->
            <div class="flex-shrink-0 w-12 h-12 glass-strong rounded-xl flex items-center justify-center group-hover:animate-glow">
              <component :is="feature.icon" class="w-6 h-6 text-electric-400" />
            </div>
            
            <!-- Content -->
            <div>
              <h3 class="text-xl font-semibold text-white mb-2">
                {{ feature.title }}
              </h3>
              <p class="text-gray-300">
                {{ feature.description }}
              </p>
            </div>
          </div>
        </div>
        
        <!-- Right Column - Visual -->
        <div class="relative">
          <div class="glass-strong rounded-3xl p-8 text-center">
            <!-- Cost Guarantee Card -->
            <div class="glass-card rounded-2xl p-6 mb-8">
              <div class="text-4xl font-bold text-electric-400 mb-2">5 Years</div>
              <div class="text-gray-300 mb-4">Cost Guarantee</div>
              <div class="text-sm text-gray-400">
                Predictable operational costs with no fuel price fluctuations
              </div>
            </div>
            
            <!-- Network Coverage -->
            <div class="space-y-4">
              <h4 class="text-lg font-semibold text-white">Geographic Coverage</h4>
              <div class="grid grid-cols-2 gap-4">
                <div class="glass-card rounded-xl p-4 text-center">
                  <div class="text-2xl font-bold text-electric-400">100+</div>
                  <div class="text-sm text-gray-300">Charging Points</div>
                </div>
                <div class="glass-card rounded-xl p-4 text-center">
                  <div class="text-2xl font-bold text-electric-400">24/7</div>
                  <div class="text-sm text-gray-300">Access</div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <!-- Benefits Highlight -->
      <div class="mt-20 glass-strong rounded-3xl p-8 md:p-12">
        <div class="text-center mb-12">
          <h3 class="text-3xl md:text-4xl font-bold text-white mb-6">
            Partnering with the world's best electric vehicle OEM's
          </h3>
          <p class="text-lg text-gray-300 max-w-4xl mx-auto">
            We're making sure you always have access to the best technology with none of the upfront costs.
          </p>
        </div>
        
        <!-- Single Invoice Promise -->
        <div class="glass-card rounded-2xl p-8 text-center max-w-4xl mx-auto">
          <div class="text-2xl font-bold text-white mb-4">
            Single Monthly Invoice
          </div>
          <p class="text-gray-300 text-lg">
            Our solution includes all your monthly operational electricity costs. It's all included in a single monthly invoice that suits your specific operational needs.
          </p>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { 
  MapPinIcon, 
  ClockIcon, 
  CurrencyDollarIcon, 
  ChartBarIcon,
  ShieldCheckIcon,
  BoltIcon
} from '@heroicons/vue/24/outline'

const features = [
  {
    icon: MapPinIcon,
    title: "Geographically Distributed Network",
    description: "Our charging network solves your fleet's range anxiety with strategically placed charging points across all operational areas."
  },
  {
    icon: CurrencyDollarIcon,
    title: "Zero CAPEX on Infrastructure",
    description: "No need to spend any capital expenditure on charging infrastructure. We handle all the setup and maintenance."
  },
  {
    icon: ChartBarIcon,
    title: "Decoupled Operational Costs",
    description: "Investing in electricity instead of fuel results in decoupling of operational costs from unpredictable fuel price fluctuations."
  },
  {
    icon: ShieldCheckIcon,
    title: "Technology Risk Mitigation",
    description: "Access to the latest EV technology without the risk of owning outdated equipment as technology evolves."
  },
  {
    icon: BoltIcon,
    title: "Comprehensive Energy Solution",
    description: "All your energy needs are covered - from vehicle charging to operational electricity requirements."
  },
  {
    icon: ClockIcon,
    title: "24/7 Support & Maintenance",
    description: "Round-the-clock support ensures your fleet is always operational with minimal downtime."
  }
]
</script>
