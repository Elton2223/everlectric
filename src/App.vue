<template>
  <div class="min-h-screen bg-gradient-to-br from-slate-900 via-blue-900 to-slate-900">
    <!-- Navigation -->
    <NavBar />
    
    <!-- Hero Section -->
    <HeroSection />
    
    <!-- Services Section -->
    <ServicesSection />
    
    <!-- Features Section -->
    <FeaturesSection />
    
    <!-- Benefits Section -->
    <BenefitsSection />
    
    <!-- Testimonials Section -->
    <TestimonialsSection />
    
    <!-- Pricing Calculator Section -->
    <PricingCalculator />
    
    <!-- FAQ Section -->
    <FAQSection />
    
    <!-- Newsletter Signup -->
    <NewsletterSignup />
    
    <!-- Partners Section -->
    <PartnersSection />
    
    <!-- Contact Section -->
    <ContactSection />
    
    <!-- Footer -->
    <Footer />
    
    <!-- Scroll to Top Button -->
    <ScrollToTop />
    
    <!-- Cookie Consent -->
    <CookieConsent />
  </div>
</template>

<script setup>
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import ServicesSection from './components/ServicesSection.vue'
import FeaturesSection from './components/FeaturesSection.vue'
import BenefitsSection from './components/BenefitsSection.vue'
import TestimonialsSection from './components/TestimonialsSection.vue'
import PricingCalculator from './components/PricingCalculator.vue'
import FAQSection from './components/FAQSection.vue'
import NewsletterSignup from './components/NewsletterSignup.vue'
import PartnersSection from './components/PartnersSection.vue'
import ContactSection from './components/ContactSection.vue'
import Footer from './components/Footer.vue'
import ScrollToTop from './components/ScrollToTop.vue'
import CookieConsent from './components/CookieConsent.vue'
</script>
