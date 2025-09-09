<template>
  <section class="py-16 relative">
    <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="glass-strong rounded-3xl p-8 md:p-12 text-center">
        <h2 class="text-3xl md:text-4xl font-bold text-white mb-4">
          Stay Updated with Everlectric
        </h2>
        <p class="text-lg text-gray-300 mb-8 max-w-2xl mx-auto">
          Get the latest news about electric vehicles, charging infrastructure, and sustainable fleet solutions delivered to your inbox.
        </p>
        
        <form @submit.prevent="subscribe" class="max-w-md mx-auto">
          <div class="flex flex-col sm:flex-row gap-4">
            <div class="flex-1">
              <input
                v-model="email"
                type="email"
                placeholder="Enter your email address"
                class="w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400"
                :class="{ 'border-red-500': error }"
                required
              />
              <p v-if="error" class="text-red-400 text-sm mt-1">{{ error }}</p>
            </div>
            <button
              type="submit"
              :disabled="isSubmitting"
              class="glass-strong px-8 py-3 rounded-lg text-white font-semibold hover:bg-white/20 transition-all duration-300 electric-glow disabled:opacity-50 disabled:cursor-not-allowed"
            >
              {{ isSubmitting ? 'Subscribing...' : 'Subscribe' }}
            </button>
          </div>
          
          <!-- Success Message -->
          <div v-if="showSuccess" class="mt-4 glass-card rounded-lg p-4 bg-green-500/20 border border-green-500/30">
            <div class="flex items-center justify-center">
              <div class="w-5 h-5 text-green-400 mr-2">✓</div>
              <p class="text-green-300">Thank you for subscribing! Check your email for confirmation.</p>
            </div>
          </div>
        </form>
        
        <p class="text-sm text-gray-400 mt-6">
          We respect your privacy. Unsubscribe at any time.
          <a href="/privacy-policy" class="text-electric-400 hover:text-electric-300 underline">Privacy Policy</a>
        </p>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const email = ref('')
const isSubmitting = ref(false)
const showSuccess = ref(false)
const error = ref('')

const subscribe = async () => {
  if (!email.value) {
    error.value = 'Please enter your email address'
    return
  }
  
  if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email.value)) {
    error.value = 'Please enter a valid email address'
    return
  }
  
  isSubmitting.value = true
  error.value = ''
  
  try {
    // Simulate API call
    await new Promise(resolve => setTimeout(resolve, 2000))
    
    // In a real application, you would send the email to your backend
    console.log('Newsletter subscription:', email.value)
    
    showSuccess.value = true
    email.value = ''
    
    // Hide success message after 5 seconds
    setTimeout(() => {
      showSuccess.value = false
    }, 5000)
    
  } catch (err) {
    error.value = 'Something went wrong. Please try again.'
  } finally {
    isSubmitting.value = false
  }
}
</script>
