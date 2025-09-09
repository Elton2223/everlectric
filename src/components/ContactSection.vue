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
              <button 
                @click="scheduleCall"
                class="w-full glass-strong px-4 py-3 rounded-lg text-white font-medium hover:bg-white/20 transition-all duration-300 text-left"
              >
                📞 Schedule a Call
              </button>
              <button 
                @click="sendEmail"
                class="w-full glass-strong px-4 py-3 rounded-lg text-white font-medium hover:bg-white/20 transition-all duration-300 text-left"
              >
                📧 Send Email
              </button>
              <button 
                @click="requestQuote"
                class="w-full glass-strong px-4 py-3 rounded-lg text-white font-medium hover:bg-white/20 transition-all duration-300 text-left"
              >
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
                  :class="[
                    'w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400',
                    errors.firstName ? 'border-red-500 focus:ring-red-500' : ''
                  ]"
                  placeholder="John"
                  required
                />
                <p v-if="errors.firstName" class="text-red-400 text-sm mt-1">{{ errors.firstName }}</p>
              </div>
              <div>
                <label class="block text-sm font-medium text-gray-300 mb-2">Last Name</label>
                <input 
                  v-model="form.lastName"
                  type="text" 
                  :class="[
                    'w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400',
                    errors.lastName ? 'border-red-500 focus:ring-red-500' : ''
                  ]"
                  placeholder="Doe"
                  required
                />
                <p v-if="errors.lastName" class="text-red-400 text-sm mt-1">{{ errors.lastName }}</p>
              </div>
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-300 mb-2">Email</label>
              <input 
                v-model="form.email"
                type="email" 
                :class="[
                  'w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400',
                  errors.email ? 'border-red-500 focus:ring-red-500' : ''
                ]"
                placeholder="john@company.com"
                required
              />
              <p v-if="errors.email" class="text-red-400 text-sm mt-1">{{ errors.email }}</p>
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-300 mb-2">Company</label>
              <input 
                v-model="form.company"
                type="text" 
                :class="[
                  'w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400',
                  errors.company ? 'border-red-500 focus:ring-red-500' : ''
                ]"
                placeholder="Your Company Name"
                required
              />
              <p v-if="errors.company" class="text-red-400 text-sm mt-1">{{ errors.company }}</p>
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-300 mb-2">Fleet Size</label>
              <select 
                v-model="form.fleetSize"
                :class="[
                  'w-full glass-card px-4 py-3 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-electric-400',
                  errors.fleetSize ? 'border-red-500 focus:ring-red-500' : ''
                ]"
                required
              >
                <option value="" disabled>Select fleet size</option>
                <option value="1-5">1-5 vehicles</option>
                <option value="6-20">6-20 vehicles</option>
                <option value="21-50">21-50 vehicles</option>
                <option value="50+">50+ vehicles</option>
              </select>
              <p v-if="errors.fleetSize" class="text-red-400 text-sm mt-1">{{ errors.fleetSize }}</p>
            </div>
            
            <div>
              <label class="block text-sm font-medium text-gray-300 mb-2">Message</label>
              <textarea 
                v-model="form.message"
                rows="4"
                :class="[
                  'w-full glass-card px-4 py-3 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-electric-400',
                  errors.message ? 'border-red-500 focus:ring-red-500' : ''
                ]"
                placeholder="Tell us about your fleet requirements..."
                required
              ></textarea>
              <p v-if="errors.message" class="text-red-400 text-sm mt-1">{{ errors.message }}</p>
            </div>
            
            <!-- Success Message -->
            <div v-if="showSuccess" class="glass-card rounded-lg p-4 bg-green-500/20 border border-green-500/30">
              <div class="flex items-center">
                <div class="w-5 h-5 text-green-400 mr-3">✓</div>
                <p class="text-green-300">Thank you for your message! We'll get back to you soon.</p>
              </div>
            </div>
            
            <!-- Error Message -->
            <div v-if="errors.submit" class="glass-card rounded-lg p-4 bg-red-500/20 border border-red-500/30">
              <div class="flex items-center">
                <div class="w-5 h-5 text-red-400 mr-3">⚠</div>
                <p class="text-red-300">{{ errors.submit }}</p>
              </div>
            </div>
            
            <button 
              type="submit"
              class="w-full glass-strong px-8 py-4 rounded-lg text-white font-semibold text-lg hover:bg-white/20 transition-all duration-300 electric-glow disabled:opacity-50 disabled:cursor-not-allowed"
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
import { ref, computed } from 'vue'
import { MapPinIcon, PhoneIcon, EnvelopeIcon } from '@heroicons/vue/24/outline'

const isSubmitting = ref(false)
const showSuccess = ref(false)
const errors = ref({})

const form = ref({
  firstName: '',
  lastName: '',
  email: '',
  company: '',
  fleetSize: '',
  message: ''
})

// Form validation
const validateForm = () => {
  errors.value = {}
  
  if (!form.value.firstName.trim()) {
    errors.value.firstName = 'First name is required'
  }
  
  if (!form.value.lastName.trim()) {
    errors.value.lastName = 'Last name is required'
  }
  
  if (!form.value.email.trim()) {
    errors.value.email = 'Email is required'
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(form.value.email)) {
    errors.value.email = 'Please enter a valid email address'
  }
  
  if (!form.value.company.trim()) {
    errors.value.company = 'Company name is required'
  }
  
  if (!form.value.fleetSize) {
    errors.value.fleetSize = 'Please select your fleet size'
  }
  
  if (!form.value.message.trim()) {
    errors.value.message = 'Message is required'
  } else if (form.value.message.trim().length < 10) {
    errors.value.message = 'Message must be at least 10 characters long'
  }
  
  return Object.keys(errors.value).length === 0
}

const hasErrors = computed(() => Object.keys(errors.value).length > 0)

const submitForm = async () => {
  if (!validateForm()) {
    return
  }
  
  isSubmitting.value = true
  errors.value = {}
  
  try {
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
    
    showSuccess.value = true
    
    // Hide success message after 5 seconds
    setTimeout(() => {
      showSuccess.value = false
    }, 5000)
    
  } catch (error) {
    console.error('Form submission error:', error)
    errors.value.submit = 'There was an error submitting your form. Please try again.'
  } finally {
    isSubmitting.value = false
  }
}

// Quick action handlers
const scheduleCall = () => {
  window.open('tel:0124436455', '_self')
}

const sendEmail = () => {
  window.open('mailto:info@everlectric.co.za?subject=Inquiry about Electric Vehicle Services', '_self')
}

const requestQuote = () => {
  scrollToContact()
}

const scrollToContact = () => {
  const element = document.querySelector('#contact')
  if (element) {
    element.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    })
  }
}
</script>
