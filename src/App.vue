<template>
  <div id="app">
    <NavBar />
    <HeroSection />
    <WhySection />
    <PricingSection />
    <ReportSection />
    <HowItWorks />
    <AgenciesSection />
    <TrustSection />
    <FaqSection />
    <FooterSection />
  </div>
</template>

<script setup>
import NavBar from './components/NavBar.vue'
import HeroSection from './components/HeroSection.vue'
import WhySection from './components/WhySection.vue'
import ReportSection from './components/ReportSection.vue'
import HowItWorks from './components/HowItWorks.vue'
import PricingSection from './components/PricingSection.vue'
import AgenciesSection from './components/AgenciesSection.vue'
import TrustSection from './components/TrustSection.vue'
import FaqSection from './components/FaqSection.vue'
import FooterSection from './components/FooterSection.vue'
</script>

<style lang="scss">
@use './assets/styles/global.scss';
</style>
