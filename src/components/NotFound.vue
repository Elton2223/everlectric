<template>
  <div class="min-h-screen bg-gradient-to-br from-slate-900 via-blue-900 to-slate-900 flex items-center justify-center px-4">
    <div class="text-center max-w-2xl mx-auto">
      <!-- 404 Animation -->
      <div class="mb-8">
        <div class="text-8xl md:text-9xl font-bold text-electric-400 mb-4 animate-pulse">
          404
        </div>
        <div class="w-32 h-1 bg-gradient-to-r from-electric-400 to-blue-400 mx-auto rounded-full"></div>
      </div>
      
      <!-- Error Message -->
      <div class="glass-strong rounded-3xl p-8 md:p-12 mb-8">
        <h1 class="text-3xl md:text-4xl font-bold text-white mb-4">
          Page Not Found
        </h1>
        <p class="text-lg text-gray-300 mb-8">
          Sorry, the page you're looking for doesn't exist or has been moved. 
          Let's get you back on track to your electric future.
        </p>
        
        <!-- Action Buttons -->
        <div class="flex flex-col sm:flex-row gap-4 justify-center">
          <button 
            @click="goHome"
            class="glass-strong px-8 py-4 rounded-lg text-white font-semibold text-lg hover:bg-white/20 transition-all duration-300 electric-glow"
          >
            Go Home
          </button>
          <button 
            @click="goBack"
            class="glass px-8 py-4 rounded-lg text-white font-semibold text-lg hover:bg-white/10 transition-all duration-300"
          >
            Go Back
          </button>
        </div>
      </div>
      
      <!-- Quick Links -->
      <div class="glass-card rounded-2xl p-6">
        <h3 class="text-xl font-semibold text-white mb-4">Popular Pages</h3>
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-4">
          <a 
            href="#services" 
            @click="scrollToSection('#services')"
            class="block glass-strong px-4 py-3 rounded-lg text-white hover:bg-white/20 transition-all duration-300 text-center"
          >
            Our Services
          </a>
          <a 
            href="#features" 
            @click="scrollToSection('#features')"
            class="block glass-strong px-4 py-3 rounded-lg text-white hover:bg-white/20 transition-all duration-300 text-center"
          >
            Features
          </a>
          <a 
            href="#contact" 
            @click="scrollToSection('#contact')"
            class="block glass-strong px-4 py-3 rounded-lg text-white hover:bg-white/20 transition-all duration-300 text-center"
          >
            Contact Us
          </a>
          <a 
            href="#pricing" 
            @click="scrollToSection('#pricing')"
            class="block glass-strong px-4 py-3 rounded-lg text-white hover:bg-white/20 transition-all duration-300 text-center"
          >
            Pricing Calculator
          </a>
        </div>
      </div>
      
      <!-- Help Section -->
      <div class="mt-8 text-center">
        <p class="text-gray-400 mb-4">Need help? We're here for you</p>
        <div class="flex flex-col sm:flex-row gap-4 justify-center text-sm">
          <a 
            href="tel:0124436455" 
            class="text-electric-400 hover:text-electric-300 transition-colors duration-200"
          >
            📞 012 443 6455
          </a>
          <a 
            href="mailto:info@everlectric.co.za" 
            class="text-electric-400 hover:text-electric-300 transition-colors duration-200"
          >
            📧 info@everlectric.co.za
          </a>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()

const goHome = () => {
  // If using Vue Router, navigate to home
  if (router) {
    router.push('/')
  } else {
    // Fallback to scrolling to top
    window.scrollTo({ top: 0, behavior: 'smooth' })
  }
}

const goBack = () => {
  if (window.history.length > 1) {
    window.history.back()
  } else {
    goHome()
  }
}

const scrollToSection = (sectionId) => {
  const element = document.querySelector(sectionId)
  if (element) {
    element.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    })
  }
}
</script>
