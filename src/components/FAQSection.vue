<template>
  <section id="faq" class="py-20 relative">
    <div class="max-w-4xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
          Frequently Asked Questions
        </h2>
        <p class="text-xl text-gray-300 max-w-3xl mx-auto">
          Get answers to common questions about our electric vehicle services and solutions.
        </p>
      </div>
      
      <!-- FAQ Items -->
      <div class="space-y-4">
        <div 
          v-for="(faq, index) in faqs" 
          :key="index"
          class="glass-card rounded-2xl overflow-hidden group"
        >
          <button
            @click="toggleFAQ(index)"
            class="w-full px-6 py-6 text-left flex items-center justify-between hover:bg-white/5 transition-all duration-300"
          >
            <h3 class="text-lg font-semibold text-white pr-4">
              {{ faq.question }}
            </h3>
            <div class="flex-shrink-0">
              <svg 
                class="w-6 h-6 text-electric-400 transition-transform duration-300"
                :class="{ 'rotate-180': faq.isOpen }"
                fill="none" 
                stroke="currentColor" 
                viewBox="0 0 24 24"
              >
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
              </svg>
            </div>
          </button>
          
          <Transition name="slide-down">
            <div v-if="faq.isOpen" class="px-6 pb-6">
              <div class="border-t border-white/10 pt-4">
                <p class="text-gray-300 leading-relaxed" v-html="faq.answer"></p>
              </div>
            </div>
          </Transition>
        </div>
      </div>
      
      <!-- Contact CTA -->
      <div class="mt-16 text-center">
        <div class="glass-strong rounded-2xl p-8">
          <h3 class="text-2xl font-bold text-white mb-4">
            Still have questions?
          </h3>
          <p class="text-gray-300 mb-6">
            Our team is here to help you understand how electric vehicles can benefit your business.
          </p>
          <div class="flex flex-col sm:flex-row gap-4 justify-center">
            <button 
              @click="scrollToContact"
              class="glass-strong px-8 py-3 rounded-lg text-white font-semibold hover:bg-white/20 transition-all duration-300 electric-glow"
            >
              Contact Us
            </button>
            <button 
              @click="scheduleCall"
              class="glass px-8 py-3 rounded-lg text-white font-semibold hover:bg-white/10 transition-all duration-300"
            >
              Schedule a Call
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const faqs = ref([
  {
    question: "What is Electric Vehicle as a Service (EVaaS)?",
    answer: "EVaaS is a comprehensive solution where we provide electric vehicles, charging infrastructure, maintenance, and all operational costs in a single monthly package. You get all the benefits of electric vehicles without the upfront investment or ongoing management complexity.",
    isOpen: false
  },
  {
    question: "What are the upfront costs?",
    answer: "There are <strong>zero upfront costs</strong>. We handle all initial investments including vehicle procurement, charging infrastructure setup, and installation. You only pay a predictable monthly fee that covers everything.",
    isOpen: false
  },
  {
    question: "How does the charging network work?",
    answer: "Our geographically distributed charging network ensures your vehicles can charge wherever they need to operate. We provide 24/7 access to charging points across all operational areas, eliminating range anxiety and ensuring your fleet stays operational.",
    isOpen: false
  },
  {
    question: "What happens if a vehicle breaks down?",
    answer: "All maintenance and repairs are included in your monthly package. We provide 24/7 support and will replace vehicles if needed to ensure minimal disruption to your operations. Our goal is to keep your fleet running smoothly.",
    isOpen: false
  },
  {
    question: "How much can I save compared to traditional vehicles?",
    answer: "Our clients typically see <strong>40-70% reduction in operational costs</strong> compared to traditional fuel-powered fleets. This includes fuel savings, reduced maintenance costs, and elimination of fuel price fluctuations.",
    isOpen: false
  },
  {
    question: "What types of vehicles are available?",
    answer: "We partner with leading electric vehicle manufacturers to provide a wide range of vehicles including delivery vans, trucks, sedans, and SUVs. All vehicles are equipped with the latest technology and safety features.",
    isOpen: false
  },
  {
    question: "How long are the contracts?",
    answer: "We offer flexible contract terms starting from 24 months. Our contracts are designed to be scalable, allowing you to add or reduce vehicles based on your business needs.",
    isOpen: false
  },
  {
    question: "What about insurance and registration?",
    answer: "Everything is included in your monthly package - insurance, registration, licensing, and all administrative requirements. We handle all the paperwork so you can focus on your business.",
    isOpen: false
  },
  {
    question: "How do you ensure data security and privacy?",
    answer: "We follow strict data protection protocols and comply with all relevant privacy regulations. Your business data is encrypted and secure, and we never share your information with third parties without your explicit consent.",
    isOpen: false
  },
  {
    question: "Can I customize the service to my specific needs?",
    answer: "Absolutely! We work with you to create a customized solution that meets your specific operational requirements, including vehicle types, charging schedules, and service levels.",
    isOpen: false
  }
])

const toggleFAQ = (index) => {
  // Close all other FAQs
  faqs.value.forEach((faq, i) => {
    if (i !== index) {
      faq.isOpen = false
    }
  })
  
  // Toggle the selected FAQ
  faqs.value[index].isOpen = !faqs.value[index].isOpen
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

const scheduleCall = () => {
  window.open('tel:0124436455', '_self')
}
</script>

<style scoped>
.slide-down-enter-active,
.slide-down-leave-active {
  transition: all 0.3s ease;
  overflow: hidden;
}

.slide-down-enter-from {
  max-height: 0;
  opacity: 0;
}

.slide-down-leave-to {
  max-height: 0;
  opacity: 0;
}

.slide-down-enter-to,
.slide-down-leave-from {
  max-height: 200px;
  opacity: 1;
}
</style>
