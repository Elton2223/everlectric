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
            <a 
              href="#home" 
              @click="(e) => handleNavClick(e, '#home')"
              :class="[
                'px-3 py-2 text-sm font-medium transition-colors duration-200',
                activeSection === 'home' ? 'text-electric-400' : 'text-white hover:text-electric-400'
              ]"
            >
              Home
            </a>
            <a 
              href="#services" 
              @click="(e) => handleNavClick(e, '#services')"
              :class="[
                'px-3 py-2 text-sm font-medium transition-colors duration-200',
                activeSection === 'services' ? 'text-electric-400' : 'text-white hover:text-electric-400'
              ]"
            >
              Services
            </a>
            <a 
              href="#features" 
              @click="(e) => handleNavClick(e, '#features')"
              :class="[
                'px-3 py-2 text-sm font-medium transition-colors duration-200',
                activeSection === 'features' ? 'text-electric-400' : 'text-white hover:text-electric-400'
              ]"
            >
              Features
            </a>
            <a 
              href="#pricing" 
              @click="(e) => handleNavClick(e, '#pricing')"
              :class="[
                'px-3 py-2 text-sm font-medium transition-colors duration-200',
                activeSection === 'pricing' ? 'text-electric-400' : 'text-white hover:text-electric-400'
              ]"
            >
              Pricing
            </a>
            <a 
              href="#contact" 
              @click="(e) => handleNavClick(e, '#contact')"
              :class="[
                'px-3 py-2 text-sm font-medium transition-colors duration-200',
                activeSection === 'contact' ? 'text-electric-400' : 'text-white hover:text-electric-400'
              ]"
            >
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
        <a 
          href="#home" 
          @click="(e) => handleNavClick(e, '#home')"
          :class="[
            'block px-3 py-2 text-base font-medium transition-colors duration-200',
            activeSection === 'home' ? 'text-electric-400' : 'text-white hover:text-electric-400'
          ]"
        >
          Home
        </a>
        <a 
          href="#services" 
          @click="(e) => handleNavClick(e, '#services')"
          :class="[
            'block px-3 py-2 text-base font-medium transition-colors duration-200',
            activeSection === 'services' ? 'text-electric-400' : 'text-white hover:text-electric-400'
          ]"
        >
          Services
        </a>
        <a 
          href="#features" 
          @click="(e) => handleNavClick(e, '#features')"
          :class="[
            'block px-3 py-2 text-base font-medium transition-colors duration-200',
            activeSection === 'features' ? 'text-electric-400' : 'text-white hover:text-electric-400'
          ]"
        >
          Features
        </a>
        <a 
          href="#pricing" 
          @click="(e) => handleNavClick(e, '#pricing')"
          :class="[
            'block px-3 py-2 text-base font-medium transition-colors duration-200',
            activeSection === 'pricing' ? 'text-electric-400' : 'text-white hover:text-electric-400'
          ]"
        >
          Pricing
        </a>
        <a 
          href="#contact" 
          @click="(e) => handleNavClick(e, '#contact')"
          :class="[
            'block px-3 py-2 text-base font-medium transition-colors duration-200',
            activeSection === 'contact' ? 'text-electric-400' : 'text-white hover:text-electric-400'
          ]"
        >
          Contact
        </a>
        <button 
          @click="(e) => handleNavClick(e, '#contact')"
          class="w-full text-left glass-strong px-3 py-2 rounded-lg text-white font-medium hover:bg-white/20 transition-all duration-300"
        >
          Get Started
        </button>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const mobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}

// Smooth scrolling function
const scrollToSection = (sectionId) => {
  const element = document.querySelector(sectionId)
  if (element) {
    element.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    })
  }
  // Close mobile menu after navigation
  mobileMenuOpen.value = false
}

// Handle navigation clicks
const handleNavClick = (e, sectionId) => {
  e.preventDefault()
  scrollToSection(sectionId)
}

// Active section tracking
const activeSection = ref('home')

const updateActiveSection = () => {
  const sections = ['home', 'services', 'features', 'testimonials', 'pricing', 'faq', 'contact']
  const scrollPosition = window.scrollY + 100

  for (const section of sections) {
    const element = document.getElementById(section)
    if (element) {
      const { offsetTop, offsetHeight } = element
      if (scrollPosition >= offsetTop && scrollPosition < offsetTop + offsetHeight) {
        activeSection.value = section
        break
      }
    }
  }
}

onMounted(() => {
  window.addEventListener('scroll', updateActiveSection)
  updateActiveSection()
})

onUnmounted(() => {
  window.removeEventListener('scroll', updateActiveSection)
})
</script>
