<template>
  <section class="py-20 relative">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
          Why Choose Everlectric?
        </h2>
        <p class="text-xl text-gray-300 max-w-3xl mx-auto">
          Experience the future of fleet management with our comprehensive electric vehicle solutions.
        </p>
      </div>
      
      <!-- Benefits Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 mb-16">
        <div 
          v-for="(benefit, index) in benefits" 
          :key="index"
          class="glass-card rounded-2xl p-8 group hover:scale-105 transition-all duration-300"
          :style="{ animationDelay: `${index * 0.1}s` }"
        >
          <!-- Icon -->
          <div class="w-16 h-16 glass-strong rounded-2xl flex items-center justify-center mb-6 group-hover:animate-glow">
            <component :is="benefit.icon" class="w-8 h-8 text-electric-400" />
          </div>
          
          <!-- Title -->
          <h3 class="text-xl font-semibold text-white mb-4">
            {{ benefit.title }}
          </h3>
          
          <!-- Description -->
          <p class="text-gray-300 leading-relaxed">
            {{ benefit.description }}
          </p>
          
          <!-- Value -->
          <div class="mt-4 text-2xl font-bold text-electric-400">
            {{ benefit.value }}
          </div>
        </div>
      </div>
      
      <!-- Sustainability Focus -->
      <div class="glass-strong rounded-3xl p-8 md:p-12 text-center">
        <h3 class="text-3xl md:text-4xl font-bold text-white mb-6">
          Are you looking to transition to a sustainability and environmentally friendly alternative?
        </h3>
        
        <!-- Environmental Impact Stats -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mt-12">
          <div class="glass-card rounded-2xl p-6">
            <div class="text-4xl font-bold text-electric-400 mb-2">0</div>
            <div class="text-gray-300 mb-2">Direct Emissions</div>
            <div class="text-sm text-gray-400">Zero tailpipe emissions from your fleet</div>
          </div>
          
          <div class="glass-card rounded-2xl p-6">
            <div class="text-4xl font-bold text-electric-400 mb-2">-70%</div>
            <div class="text-gray-300 mb-2">Carbon Footprint</div>
            <div class="text-sm text-gray-400">Reduction compared to traditional fleets</div>
          </div>
          
          <div class="glass-card rounded-2xl p-6">
            <div class="text-4xl font-bold text-electric-400 mb-2">100%</div>
            <div class="text-gray-300 mb-2">Renewable Energy</div>
            <div class="text-sm text-gray-400">Powered by clean energy sources</div>
          </div>
        </div>
        
        <!-- CTA -->
        <div class="mt-12">
          <button class="glass-strong px-8 py-4 rounded-full text-white font-semibold text-lg hover:bg-white/20 transition-all duration-300 electric-glow">
            Start Your Green Journey
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { 
  HeartIcon, 
  CurrencyDollarIcon, 
  ClockIcon, 
  ShieldCheckIcon, 
  BoltIcon, 
  ChartBarIcon 
} from '@heroicons/vue/24/outline'

const benefits = [
  {
    icon: HeartIcon,
    title: "Environmental Impact",
    description: "Reduce your carbon footprint and contribute to a cleaner future with zero-emission vehicles.",
    value: "100% Clean"
  },
  {
    icon: CurrencyDollarIcon,
    title: "Cost Savings",
    description: "Significant reduction in operational costs with predictable electricity pricing and no fuel costs.",
    value: "Save 40%"
  },
  {
    icon: ClockIcon,
    title: "Operational Efficiency",
    description: "Streamlined fleet management with automated charging and maintenance scheduling.",
    value: "24/7 Uptime"
  },
  {
    icon: ShieldCheckIcon,
    title: "Risk Mitigation",
    description: "No technology risk, no maintenance costs, and no fuel price fluctuations to worry about.",
    value: "Zero Risk"
  },
  {
    icon: BoltIcon,
    title: "Future-Proof Technology",
    description: "Always have access to the latest EV technology without the burden of ownership.",
    value: "Always Latest"
  },
  {
    icon: ChartBarIcon,
    title: "Scalable Solution",
    description: "Easily scale your fleet up or down based on your business needs with flexible packages.",
    value: "Flexible"
  }
]
</script>
