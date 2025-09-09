<template>
  <nav class="fixed top-0 w-full z-50 glass-strong">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex justify-between items-center h-16">
        <!-- Logo -->
        <div class="flex-shrink-0">
          <h1 class="text-2xl font-bold text-white">
            <span class="text-electric-400">Ever</span>lectric
          </h1>
        </div>
        
        <!-- Desktop Navigation -->
        <div class="hidden md:block">
          <div class="ml-10 flex items-baseline space-x-8">
            <a href="#home" class="text-white hover:text-electric-400 px-3 py-2 text-sm font-medium transition-colors duration-200">
              Home
            </a>
            <a href="#services" class="text-white hover:text-electric-400 px-3 py-2 text-sm font-medium transition-colors duration-200">
              Services
            </a>
            <a href="#features" class="text-white hover:text-electric-400 px-3 py-2 text-sm font-medium transition-colors duration-200">
              Features
            </a>
            <a href="#contact" class="text-white hover:text-electric-400 px-3 py-2 text-sm font-medium transition-colors duration-200">
              Contact
            </a>
          </div>
        </div>
        
        <!-- CTA Button -->
        <div class="hidden md:block">
          <button class="glass-strong px-6 py-2 rounded-full text-white font-medium hover:bg-white/20 transition-all duration-300 electric-glow">
            Get Started
          </button>
        </div>
        
        <!-- Mobile menu button -->
        <div class="md:hidden">
          <button @click="toggleMobileMenu" class="text-white hover:text-electric-400 focus:outline-none">
            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path v-if="!mobileMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
              <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
      </div>
    </div>
    
    <!-- Mobile Navigation -->
    <div v-if="mobileMenuOpen" class="md:hidden glass-strong">
      <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
        <a href="#home" class="text-white hover:text-electric-400 block px-3 py-2 text-base font-medium">Home</a>
        <a href="#services" class="text-white hover:text-electric-400 block px-3 py-2 text-base font-medium">Services</a>
        <a href="#features" class="text-white hover:text-electric-400 block px-3 py-2 text-base font-medium">Features</a>
        <a href="#contact" class="text-white hover:text-electric-400 block px-3 py-2 text-base font-medium">Contact</a>
        <button class="w-full text-left glass-strong px-3 py-2 rounded-lg text-white font-medium hover:bg-white/20 transition-all duration-300">
          Get Started
        </button>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref } from 'vue'

const mobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}
</script>
