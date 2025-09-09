<template>
  <section id="home" class="relative min-h-screen flex items-center justify-center overflow-hidden">
    <!-- Animated Background -->
    <div class="absolute inset-0">
      <div class="absolute inset-0 bg-gradient-to-br from-blue-600/20 via-electric-500/20 to-blue-800/20"></div>
      <div class="absolute top-1/4 left-1/4 w-96 h-96 bg-electric-400/10 rounded-full blur-3xl animate-float"></div>
      <div class="absolute bottom-1/4 right-1/4 w-80 h-80 bg-blue-400/10 rounded-full blur-3xl animate-float" style="animation-delay: -3s;"></div>
      <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 w-64 h-64 bg-primary-400/10 rounded-full blur-3xl animate-float" style="animation-delay: -1.5s;"></div>
    </div>
    
    <div class="relative z-10 max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
      <div class="glass-strong rounded-3xl p-8 md:p-12 lg:p-16 max-w-5xl mx-auto">
        <!-- Main Heading -->
        <h1 class="text-4xl md:text-6xl lg:text-7xl font-bold mb-6 animate-fade-in">
          <span class="bg-gradient-to-r from-white via-electric-300 to-blue-300 bg-clip-text text-transparent">
            Powering Your Journey
          </span>
        </h1>
        
        <!-- Subheading -->
        <p class="text-xl md:text-2xl lg:text-3xl text-gray-300 mb-8 animate-slide-up" style="animation-delay: 0.2s;">
          Let us focus on the electric vehicles & charging technology while you focus on delivering to your clients.
        </p>
        
        <!-- Description -->
        <p class="text-lg md:text-xl text-gray-400 mb-12 max-w-4xl mx-auto animate-slide-up" style="animation-delay: 0.4s;">
          We're packaging leading international electric vehicles, charging infrastructure & innovative finance solutions that remove all the hurdles to adopting a cleaner & more efficient future. Our service makes your fleet's transition to electric vehicles as painless as possible.
        </p>
        
        <!-- CTA Buttons -->
        <div class="flex flex-col sm:flex-row gap-4 justify-center items-center animate-slide-up" style="animation-delay: 0.6s;">
          <button 
            @click="scrollToContact"
            class="glass-strong px-8 py-4 rounded-full text-white font-semibold text-lg hover:bg-white/20 transition-all duration-300 electric-glow"
          >
            Start Your Journey
          </button>
          <button 
            @click="scrollToServices"
            class="glass px-8 py-4 rounded-full text-white font-semibold text-lg hover:bg-white/10 transition-all duration-300"
          >
            Learn More
          </button>
        </div>
        
        <!-- Stats -->
        <div class="grid grid-cols-1 md:grid-cols-3 gap-8 mt-16 animate-slide-up" style="animation-delay: 0.8s;">
          <div class="glass-card rounded-2xl p-6 text-center">
            <div class="text-3xl md:text-4xl font-bold text-electric-400 mb-2">0%</div>
            <div class="text-gray-300">Upfront Investment</div>
          </div>
          <div class="glass-card rounded-2xl p-6 text-center">
            <div class="text-3xl md:text-4xl font-bold text-electric-400 mb-2">100%</div>
            <div class="text-gray-300">Electric Fuel Included</div>
          </div>
          <div class="glass-card rounded-2xl p-6 text-center">
            <div class="text-3xl md:text-4xl font-bold text-electric-400 mb-2">∞</div>
            <div class="text-gray-300">Charging Network</div>
          </div>
        </div>
      </div>
    </div>
    
    <!-- Scroll Indicator -->
    <div class="absolute bottom-8 left-1/2 transform -translate-x-1/2 animate-bounce">
      <div class="w-6 h-10 border-2 border-white/30 rounded-full flex justify-center">
        <div class="w-1 h-3 bg-white/50 rounded-full mt-2 animate-pulse"></div>
      </div>
    </div>
  </section>
</template>

<script setup>
// Smooth scrolling functions
const scrollToContact = () => {
  const element = document.querySelector('#contact')
  if (element) {
    element.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    })
  }
}

const scrollToServices = () => {
  const element = document.querySelector('#services')
  if (element) {
    element.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    })
  }
}
</script>
