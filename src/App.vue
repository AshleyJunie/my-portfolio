<script setup>
import Navbar from './components/Navbar.vue'
import HeroSection from './components/HeroSection.vue'
import AboutSection from './components/AboutSection.vue'
import EducationSection from './components/EducationSection.vue'
import PortfolioShowcaseSection from './components/PortfolioShowcaseSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import ContactSection from './components/ContactSection.vue'
import FooterSection from './components/FooterSection.vue'
</script>

<template>
  <div class="min-h-screen w-full bg-slate-950 text-white">
    <Navbar />
    <HeroSection />
    <AboutSection />
    <EducationSection />
    <ExperienceSection />
    <PortfolioShowcaseSection />
    <ContactSection />
    <FooterSection />
  </div>
</template>