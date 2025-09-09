<template>
  <section id="contact" class="py-20 relative">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
          Say Hello
        </h2>
        <p class="text-xl text-gray-300 max-w-3xl mx-auto">
          Ready to transform your fleet? Get in touch with our team to start your electric journey.
        </p>
      </div>
      
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
        <!-- Contact Information -->
        <div class="space-y-8">
          <div class="glass-strong rounded-3xl p-8">
            <h3 class="text-2xl font-bold text-white mb-6">Get in Touch</h3>
            
            <!-- Contact Details -->
            <div class="space-y-6">
              <div class="flex items-start space-x-4">
                <div class="w-12 h-12 glass-strong rounded-xl flex items-center justify-center flex-shrink-0">
                  <MapPinIcon class="w-6 h-6 text-electric-400" />
                </div>
                <div>
                  <h4 class="text-lg font-semibold text-white mb-1">Address</h4>
                  <p class="text-gray-300">
                    210 Amarand Avenue<br>
                    Pegasus Building 1<br>
                    Menlyn Maine, Pretoria
                  </p>
                </div>
              </div>
              
              <div class="flex items-start space-x-4">
                <div class="w-12 h-12 glass-strong rounded-xl flex items-center justify-center flex-shrink-0">
                  <PhoneIcon class="w-6 h-6 text-electric-400" />
                </div>
                <div>
                  <h4 class="text-lg font-semibold text-white mb-1">Phone</h4>
                  <p class="text-gray-300">012 443 6455</p>
                </div>
              </div>
              
              <div class="flex items-start space-x-4">
                <div class="w-12 h-12 glass-strong rounded-xl flex items-center justify-center flex-shrink-0">
                  <EnvelopeIcon class="w-6 h-6 text-electric-400" />
                </div>
                <div>
                  <h4 class="text-lg font-semibold text-white mb-1">Email</h4>
                  <p class="text-gray-300">info@everlectric.co.za</p>
                </div>
              </div>
            </div>
          </div>
          
          <!-- Quick Actions -->
          <div class="glass-card rounded-2xl p-6">
            <h4 class="text-lg font-semibold text-white mb-4">Quick Actions</h4>
            <div class="space-y-3">
              <button class="w-full glass-strong px-4 py-3 rounded-lg text-white font-medium hover:bg-white/20 transition-all duration-300 text-left">
                📞 Schedule a Call
              </button>
              <button class="w-full glass-strong px-4 py-3 rounded-lg text-white font-medium hover:bg-white/20 transition-all duration-300 text-left">
                📧 Send Email
              </button>
              <button class="w-full glass-strong px-4 py-3 rounded-lg text-white font-medium hover:bg-white/20 transition-all duration-300 text-left">
                📋 Request Quote
              </button>
            </div>
          </div>
        </div>
        
        <!-- Contact Form -->
        <div class="glass-strong rounded-3xl p-8">
          <h3 class="text-2xl font-bold text-white mb-6">Send us a Message</h3>
          
          <form @submit.prevent="submitForm" class="space-y-6">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div>
                <label class="block text-sm font-medium text-gray-300 mb-2">First Name</label>
                <input 
                  v-model="form.firstName"
                  type="text" 
                  class="w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400"
                  placeholder="John"
                  required
                />
              </div>
              <div>
                <label class="block text-sm font-medium text-gray-300 mb-2">Last Name</label>
                <input 
                  v-model="form.lastName"
                  type="text" 
                  class="w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400"
                  placeholder="Doe"
                  required
                />
              </div>
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-300 mb-2">Email</label>
              <input 
                v-model="form.email"
                type="email" 
                class="w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400"
                placeholder="john@company.com"
                required
              />
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-300 mb-2">Company</label>
              <input 
                v-model="form.company"
                type="text" 
                class="w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400"
                placeholder="Your Company Name"
                required
              />
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-300 mb-2">Fleet Size</label>
              <select 
                v-model="form.fleetSize"
                class="w-full glass-card px-4 py-3 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-electric-400"
                required
              >
                <option value="" disabled>Select fleet size</option>
                <option value="1-5">1-5 vehicles</option>
                <option value="6-20">6-20 vehicles</option>
                <option value="21-50">21-50 vehicles</option>
                <option value="50+">50+ vehicles</option>
              </select>
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-300 mb-2">Message</label>
              <textarea 
                v-model="form.message"
                rows="4"
                class="w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400"
                placeholder="Tell us about your fleet requirements..."
                required
              ></textarea>
            </div>
            
            <button 
              type="submit"
              class="w-full glass-strong px-8 py-4 rounded-lg text-white font-semibold text-lg hover:bg-white/20 transition-all duration-300 electric-glow"
              :disabled="isSubmitting"
            >
              {{ isSubmitting ? 'Sending...' : 'Send Message' }}
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'
import { MapPinIcon, PhoneIcon, EnvelopeIcon } from '@heroicons/vue/24/outline'

const isSubmitting = ref(false)

const form = ref({
  firstName: '',
  lastName: '',
  email: '',
  company: '',
  fleetSize: '',
  message: ''
})

const submitForm = async () => {
  isSubmitting.value = true
  
  // Simulate form submission
  await new Promise(resolve => setTimeout(resolve, 2000))
  
  // Reset form
  form.value = {
    firstName: '',
    lastName: '',
    email: '',
    company: '',
    fleetSize: '',
    message: ''
  }
  
  isSubmitting.value = false
  
  // Show success message (you could implement a toast notification here)
  alert('Thank you for your message! We\'ll get back to you soon.')
}
</script>
