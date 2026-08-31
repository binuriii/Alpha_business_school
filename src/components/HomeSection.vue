<script setup>
import HeroSection from './HeroSection.vue'
import BentoGrid from './BentoGrid.vue'
import LegacyTimeline from './LegacyTimeline.vue'
import PopularCourses from './PopularCourses.vue'
import EssentialSkillsSection from './EssentialSkillsSection.vue'
import StudentStories from './StudentStories.vue'
import WhyAlpha from './WhyAlpha.vue'
import TrendingCourses from './TrendingCourses.vue'
import CareerPathway from './CareerPathway.vue'
import BannerOne from './BannerOne.vue'
import PartnerLogosMarquee from './PartnerLogosMarquee.vue'
import SeoFooter from './SeoFooter.vue'
import CardSection from './CardSection.vue'
import ServicesSection from './ServicesSection.vue'

</script>

<template>
  <HeroSection />
  <div class="page">
    <PartnerLogosMarquee />
    <EssentialSkillsSection />
    <LegacyTimeline />
    <PopularCourses />
    <WhyAlpha />
    <TrendingCourses /> 
    <BannerOne />
    <CareerPathway />
    <StudentStories />
    <ServicesSection />
  </div>
  <SeoFooter />
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Urbanist:wght@400;500;600;700&display=swap');

:global(body, html) {
  margin: 0 !important;
  padding: 0 !important;
  width: 100%;
  overflow-x: hidden;
  font-family: 'Oakes Grotesk', 'Urbanist', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

* {
  box-sizing: border-box;
}

.page {
  width: 100%;
  min-height: 100vh;
  padding: 5% 3% 5% 3%; 
  background: #ffffff;
  font-family: 'Oakes Grotesk', 'Urbanist', sans-serif;
  box-sizing: border-box;
}
</style>