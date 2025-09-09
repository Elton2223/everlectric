<template>
  <section id="testimonials" class="py-20 relative">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <!-- Section Header -->
      <div class="text-center mb-16">
        <h2 class="text-4xl md:text-5xl font-bold text-white mb-6">
          What Our Clients Say
        </h2>
        <p class="text-xl text-gray-300 max-w-3xl mx-auto">
          Don't just take our word for it. Here's what industry leaders say about our electric vehicle solutions.
        </p>
      </div>
      
      <!-- Testimonials Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8 mb-16">
        <div 
          v-for="(testimonial, index) in testimonials" 
          :key="index"
          class="glass-card rounded-2xl p-8 group hover:scale-105 transition-all duration-300"
          :style="{ animationDelay: `${index * 0.1}s` }"
        >
          <!-- Quote Icon -->
          <div class="w-12 h-12 glass-strong rounded-xl flex items-center justify-center mb-6 group-hover:animate-glow">
            <svg class="w-6 h-6 text-electric-400" fill="currentColor" viewBox="0 0 24 24">
              <path d="M14.017 21v-7.391c0-5.704 3.731-9.57 8.983-10.609l.995 2.151c-2.432.917-3.995 3.638-3.995 5.849h4v10h-9.983zm-14.017 0v-7.391c0-5.704 3.748-9.57 9-10.609l.996 2.151c-2.433.917-3.996 3.638-3.996 5.849h4v10h-10z"/>
            </svg>
          </div>
          
          <!-- Testimonial Text -->
          <blockquote class="text-gray-300 mb-6 leading-relaxed">
            "{{ testimonial.quote }}"
          </blockquote>
          
          <!-- Author Info -->
          <div class="flex items-center">
            <div class="w-12 h-12 glass-strong rounded-full flex items-center justify-center mr-4">
              <span class="text-lg font-semibold text-electric-400">
                {{ testimonial.author.name.charAt(0) }}
              </span>
            </div>
            <div>
              <div class="font-semibold text-white">{{ testimonial.author.name }}</div>
              <div class="text-sm text-gray-400">{{ testimonial.author.position }}</div>
              <div class="text-sm text-electric-400">{{ testimonial.author.company }}</div>
            </div>
          </div>
          
          <!-- Rating -->
          <div class="flex items-center mt-4">
            <div class="flex space-x-1">
              <svg 
                v-for="i in 5" 
                :key="i" 
                class="w-4 h-4 text-yellow-400" 
                fill="currentColor" 
                viewBox="0 0 20 20"
              >
                <path d="M9.049 2.927c.3-.921 1.603-.921 1.902 0l1.07 3.292a1 1 0 00.95.69h3.462c.969 0 1.371 1.24.588 1.81l-2.8 2.034a1 1 0 00-.364 1.118l1.07 3.292c.3.921-.755 1.688-1.54 1.118l-2.8-2.034a1 1 0 00-1.175 0l-2.8 2.034c-.784.57-1.838-.197-1.539-1.118l1.07-3.292a1 1 0 00-.364-1.118L2.98 8.72c-.783-.57-.38-1.81.588-1.81h3.461a1 1 0 00.951-.69l1.07-3.292z"/>
              </svg>
            </div>
            <span class="text-sm text-gray-400 ml-2">{{ testimonial.rating }}/5</span>
          </div>
        </div>
      </div>
      
      <!-- Stats Section -->
      <div class="glass-strong rounded-3xl p-8 md:p-12">
        <div class="text-center mb-12">
          <h3 class="text-3xl md:text-4xl font-bold text-white mb-6">
            Trusted by Industry Leaders
          </h3>
          <p class="text-lg text-gray-300 max-w-4xl mx-auto">
            Our electric vehicle solutions have helped companies across South Africa reduce costs and carbon emissions.
          </p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
          <div class="text-center">
            <div class="text-4xl font-bold text-electric-400 mb-2">500+</div>
            <div class="text-gray-300 mb-1">Fleet Vehicles</div>
            <div class="text-sm text-gray-400">Successfully electrified</div>
          </div>
          
          <div class="text-center">
            <div class="text-4xl font-bold text-electric-400 mb-2">50+</div>
            <div class="text-gray-300 mb-1">Happy Clients</div>
            <div class="text-sm text-gray-400">Across South Africa</div>
          </div>
          
          <div class="text-center">
            <div class="text-4xl font-bold text-electric-400 mb-2">70%</div>
            <div class="text-gray-300 mb-1">Cost Reduction</div>
            <div class="text-sm text-gray-400">Average savings</div>
          </div>
          
          <div class="text-center">
            <div class="text-4xl font-bold text-electric-400 mb-2">1000+</div>
            <div class="text-gray-300 mb-1">Tons CO₂ Saved</div>
            <div class="text-sm text-gray-400">Environmental impact</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const testimonials = [
  {
    quote: "Everlectric transformed our fleet operations completely. The zero upfront cost model made it easy to transition, and we've seen a 60% reduction in operational costs within the first year.",
    author: {
      name: "Sarah Johnson",
      position: "Fleet Manager",
      company: "Logistics Solutions SA"
    },
    rating: 5
  },
  {
    quote: "The charging infrastructure is incredibly reliable. Our drivers never worry about range anxiety, and the 24/7 support ensures our operations run smoothly. Highly recommended!",
    author: {
      name: "Michael Chen",
      position: "Operations Director",
      company: "Urban Delivery Co"
    },
    rating: 5
  },
  {
    quote: "Switching to electric vehicles with Everlectric was the best business decision we made. The environmental impact is significant, and our customers appreciate our commitment to sustainability.",
    author: {
      name: "Amanda Williams",
      position: "CEO",
      company: "Green Transport Ltd"
    },
    rating: 5
  },
  {
    quote: "The technology is always up-to-date, and we never have to worry about maintenance costs. Everlectric handles everything, allowing us to focus on our core business.",
    author: {
      name: "David Rodriguez",
      position: "Fleet Director",
      company: "City Services Group"
    },
    rating: 5
  },
  {
    quote: "The single monthly invoice makes budgeting so much easier. No more fuel price fluctuations or unexpected maintenance costs. It's exactly what we needed.",
    author: {
      name: "Lisa Thompson",
      position: "Finance Manager",
      company: "Regional Logistics"
    },
    rating: 5
  },
  {
    quote: "Everlectric's team provided excellent support throughout the transition. They made the process seamless and our drivers adapted quickly to the new vehicles.",
    author: {
      name: "James Wilson",
      position: "Operations Manager",
      company: "Express Delivery SA"
    },
    rating: 5
  }
]
</script>
