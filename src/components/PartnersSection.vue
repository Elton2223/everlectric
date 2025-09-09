<template>
  <section class="py-20 relative">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
          Trusted by Industry Leaders
        </h2>
        <p class="text-xl text-gray-300 max-w-3xl mx-auto">
          We partner with the world's leading electric vehicle manufacturers and technology providers.
        </p>
      </div>
      
      <!-- Partners Grid -->
      <div class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-6 gap-8 mb-16">
        <div 
          v-for="(partner, index) in partners" 
          :key="index"
          class="glass-card rounded-2xl p-6 flex items-center justify-center group hover:scale-110 transition-all duration-300"
          :style="{ animationDelay: `${index * 0.1}s` }"
        >
          <div class="text-2xl font-bold text-gray-400 group-hover:text-electric-400 transition-colors duration-300">
            {{ partner.name }}
          </div>
        </div>
      </div>
      
      <!-- Technology Stack -->
      <div class="glass-strong rounded-3xl p-8 md:p-12">
        <div class="text-center mb-12">
          <h3 class="text-3xl md:text-4xl font-bold text-white mb-6">
            Cutting-Edge Technology Stack
          </h3>
          <p class="text-lg text-gray-300 max-w-4xl mx-auto">
            Our comprehensive solution integrates the best in electric vehicle technology, charging infrastructure, and fleet management systems.
          </p>
        </div>
        
        <!-- Technology Categories -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
          <div class="glass-card rounded-2xl p-6 text-center">
            <div class="w-16 h-16 glass-strong rounded-2xl flex items-center justify-center mx-auto mb-4">
              <BoltIcon class="w-8 h-8 text-electric-400" />
            </div>
            <h4 class="text-xl font-semibold text-white mb-3">EV Technology</h4>
            <p class="text-gray-300 text-sm">
              Latest electric vehicle models from leading manufacturers with advanced battery technology and autonomous features.
            </p>
          </div>
          
          <div class="glass-card rounded-2xl p-6 text-center">
            <div class="w-16 h-16 glass-strong rounded-2xl flex items-center justify-center mx-auto mb-4">
              <CogIcon class="w-8 h-8 text-electric-400" />
            </div>
            <h4 class="text-xl font-semibold text-white mb-3">Charging Infrastructure</h4>
            <p class="text-gray-300 text-sm">
              Fast-charging network with smart grid integration and renewable energy sources for maximum efficiency.
            </p>
          </div>
          
          <div class="glass-card rounded-2xl p-6 text-center">
            <div class="w-16 h-16 glass-strong rounded-2xl flex items-center justify-center mx-auto mb-4">
              <ChartBarIcon class="w-8 h-8 text-electric-400" />
            </div>
            <h4 class="text-xl font-semibold text-white mb-3">Fleet Management</h4>
            <p class="text-gray-300 text-sm">
              Advanced analytics and monitoring systems for optimal fleet performance and predictive maintenance.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { BoltIcon, CogIcon, ChartBarIcon } from '@heroicons/vue/24/outline'

const partners = [
  { name: "Tesla" },
  { name: "BMW" },
  { name: "Mercedes" },
  { name: "Audi" },
  { name: "Volkswagen" },
  { name: "Nissan" },
  { name: "Hyundai" },
  { name: "Kia" },
  { name: "Ford" },
  { name: "Chevrolet" },
  { name: "Rivian" },
  { name: "Lucid" }
]
</script>
