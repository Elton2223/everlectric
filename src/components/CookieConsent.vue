<template>
  <Transition name="slide-up">
    <div v-if="showBanner" class="fixed bottom-0 left-0 right-0 z-50 glass-strong border-t border-white/20">
      <div class="max-w-7xl mx-auto px-4 py-4">
        <div class="flex flex-col md:flex-row items-center justify-between gap-4">
          <div class="flex-1">
            <h3 class="text-lg font-semibold text-white mb-2">Cookie Consent</h3>
            <p class="text-sm text-gray-300">
              We use cookies to enhance your browsing experience, serve personalized content, and analyze our traffic. 
              By clicking "Accept All", you consent to our use of cookies. 
              <a href="/privacy-policy" class="text-electric-400 hover:text-electric-300 underline">Learn more</a>
            </p>
          </div>
          <div class="flex gap-3">
            <button 
              @click="acceptAll"
              class="px-6 py-2 glass-strong rounded-lg text-white font-medium hover:bg-white/20 transition-all duration-300 electric-glow"
            >
              Accept All
            </button>
            <button 
              @click="acceptNecessary"
              class="px-6 py-2 glass rounded-lg text-white font-medium hover:bg-white/10 transition-all duration-300"
            >
              Necessary Only
            </button>
            <button 
              @click="openSettings"
              class="px-6 py-2 glass rounded-lg text-white font-medium hover:bg-white/10 transition-all duration-300"
            >
              Settings
            </button>
          </div>
        </div>
      </div>
    </div>
  </Transition>

  <!-- Cookie Settings Modal -->
  <Transition name="fade">
    <div v-if="showSettings" class="fixed inset-0 z-50 flex items-center justify-center p-4">
      <div class="absolute inset-0 bg-black/50 backdrop-blur-sm" @click="closeSettings"></div>
      <div class="relative glass-strong rounded-2xl p-8 max-w-2xl w-full max-h-[80vh] overflow-y-auto">
        <div class="flex items-center justify-between mb-6">
          <h2 class="text-2xl font-bold text-white">Cookie Settings</h2>
          <button @click="closeSettings" class="text-gray-400 hover:text-white">
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
        
        <div class="space-y-6">
          <div class="glass-card rounded-xl p-4">
            <div class="flex items-center justify-between mb-2">
              <h3 class="text-lg font-semibold text-white">Necessary Cookies</h3>
              <div class="w-12 h-6 bg-electric-400 rounded-full flex items-center justify-end px-1">
                <div class="w-4 h-4 bg-white rounded-full"></div>
              </div>
            </div>
            <p class="text-sm text-gray-300">These cookies are essential for the website to function properly. They cannot be disabled.</p>
          </div>
          
          <div class="glass-card rounded-xl p-4">
            <div class="flex items-center justify-between mb-2">
              <h3 class="text-lg font-semibold text-white">Analytics Cookies</h3>
              <div 
                @click="toggleAnalytics"
                class="w-12 h-6 rounded-full flex items-center px-1 cursor-pointer transition-colors duration-300"
                :class="analyticsEnabled ? 'bg-electric-400 justify-end' : 'bg-gray-600 justify-start'"
              >
                <div class="w-4 h-4 bg-white rounded-full"></div>
              </div>
            </div>
            <p class="text-sm text-gray-300">These cookies help us understand how visitors interact with our website.</p>
          </div>
          
          <div class="glass-card rounded-xl p-4">
            <div class="flex items-center justify-between mb-2">
              <h3 class="text-lg font-semibold text-white">Marketing Cookies</h3>
              <div 
                @click="toggleMarketing"
                class="w-12 h-6 rounded-full flex items-center px-1 cursor-pointer transition-colors duration-300"
                :class="marketingEnabled ? 'bg-electric-400 justify-end' : 'bg-gray-600 justify-start'"
              >
                <div class="w-4 h-4 bg-white rounded-full"></div>
              </div>
            </div>
            <p class="text-sm text-gray-300">These cookies are used to deliver personalized advertisements.</p>
          </div>
        </div>
        
        <div class="flex gap-3 mt-8">
          <button 
            @click="saveSettings"
            class="flex-1 glass-strong px-6 py-3 rounded-lg text-white font-medium hover:bg-white/20 transition-all duration-300 electric-glow"
          >
            Save Preferences
          </button>
          <button 
            @click="acceptAll"
            class="flex-1 glass px-6 py-3 rounded-lg text-white font-medium hover:bg-white/10 transition-all duration-300"
          >
            Accept All
          </button>
        </div>
      </div>
    </div>
  </Transition>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const showBanner = ref(false)
const showSettings = ref(false)
const analyticsEnabled = ref(false)
const marketingEnabled = ref(false)

const COOKIE_CONSENT_KEY = 'everlectric-cookie-consent'
const COOKIE_SETTINGS_KEY = 'everlectric-cookie-settings'

onMounted(() => {
  // Check if user has already given consent
  const consent = localStorage.getItem(COOKIE_CONSENT_KEY)
  if (!consent) {
    showBanner.value = true
  } else {
    loadSettings()
  }
})

const loadSettings = () => {
  const settings = localStorage.getItem(COOKIE_SETTINGS_KEY)
  if (settings) {
    const parsed = JSON.parse(settings)
    analyticsEnabled.value = parsed.analytics || false
    marketingEnabled.value = parsed.marketing || false
  }
}

const acceptAll = () => {
  const settings = {
    necessary: true,
    analytics: true,
    marketing: true,
    timestamp: Date.now()
  }
  
  localStorage.setItem(COOKIE_CONSENT_KEY, 'accepted')
  localStorage.setItem(COOKIE_SETTINGS_KEY, JSON.stringify(settings))
  
  showBanner.value = false
  showSettings.value = false
  
  // Initialize analytics if accepted
  if (settings.analytics) {
    initializeAnalytics()
  }
}

const acceptNecessary = () => {
  const settings = {
    necessary: true,
    analytics: false,
    marketing: false,
    timestamp: Date.now()
  }
  
  localStorage.setItem(COOKIE_CONSENT_KEY, 'accepted')
  localStorage.setItem(COOKIE_SETTINGS_KEY, JSON.stringify(settings))
  
  showBanner.value = false
}

const openSettings = () => {
  showSettings.value = true
}

const closeSettings = () => {
  showSettings.value = false
}

const toggleAnalytics = () => {
  analyticsEnabled.value = !analyticsEnabled.value
}

const toggleMarketing = () => {
  marketingEnabled.value = !marketingEnabled.value
}

const saveSettings = () => {
  const settings = {
    necessary: true,
    analytics: analyticsEnabled.value,
    marketing: marketingEnabled.value,
    timestamp: Date.now()
  }
  
  localStorage.setItem(COOKIE_CONSENT_KEY, 'accepted')
  localStorage.setItem(COOKIE_SETTINGS_KEY, JSON.stringify(settings))
  
  showBanner.value = false
  showSettings.value = false
  
  // Initialize analytics if enabled
  if (settings.analytics) {
    initializeAnalytics()
  }
}

const initializeAnalytics = () => {
  // Google Analytics initialization would go here
  console.log('Analytics initialized')
}
</script>

<style scoped>
.slide-up-enter-active,
.slide-up-leave-active {
  transition: transform 0.3s ease;
}

.slide-up-enter-from {
  transform: translateY(100%);
}

.slide-up-leave-to {
  transform: translateY(100%);
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
</style>
