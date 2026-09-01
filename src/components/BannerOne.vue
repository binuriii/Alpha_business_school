<script setup>
import { ref } from 'vue'

const bannerData = ref({
  badge: 'Your Next Step',
  title: 'Find the Qualification That Fits Your Ambition',
  description:
    'From professional qualifications to degrees in accounting, finance, business and risk, discover a pathway designed around where you want to go.',
  buttonText: 'Explore Your Options',
  buttonUrl: '#',
  bgImage:
    'https://images.unsplash.com/photo-1592114714621-ccc6cacad26b?q=80&w=2043&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
})
const handleContact = () => {
  // Add your action handler here
  console.log('Contact us clicked')
}
</script>

<template>
  <div class="ai-banner-container">
    <div 
      class="ai-banner" 
      :style="{ backgroundImage: `url(${bannerData.bgImage})` }"
    >
      <!-- FLOATING WHITE CONTENT CARD -->
      <div class="content-card">
        <span class="badge">{{ bannerData.badge }}</span>
        
        <h2 class="title">{{ bannerData.title }}</h2>
        
        <p class="description">
          {{ bannerData.description }}
        </p>
        
        <button class="contact-btn" @click="handleContact">
          {{ bannerData.buttonText }}
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* CONTAINER STYLING WITH CLAMP & VW/VH */
.ai-banner-container {
  width: 100vw;
  max-width: 100%;
  margin: 0 auto;
  padding: 5% 3% 5% 3%;
  margin-top: clamp(12px, 2vh, 24px);
  background: #ffffff;
  box-sizing: border-box;
  border-radius: clamp(8px, 1.2vw, 16px);
  font-family: 'Oakes Grotesk', 'Urbanist', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

/* MAIN CARD CONTAINER WITH BACKGROUND */
.ai-banner {
  position: relative;
  width: 100%;
  min-height: clamp(320px, 45vh, 520px);
  border-radius: clamp(12px, 1.5vw, 24px);
  overflow: hidden;
  background-size: cover;
  background-position: center right;
  background-repeat: no-repeat;
  display: flex;
  align-items: center;
  padding: clamp(16px, 3vw, 40px);
  box-sizing: border-box;
}

/* FLOATING WHITE CARD */
.content-card {
  background: #ffffff;
  width: 100%;
  max-width: clamp(280px, 28vw, 400px);
  border-radius: clamp(10px, 1.2vw, 18px);
  padding: clamp(20px, 3vh, 40px) clamp(18px, 2vw, 36px);
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  z-index: 2;
  box-sizing: border-box;
}

/* "NEW" BADGE */
.badge {
  background-color: #000000;
  color: #ffffff;
  font-size: clamp(10px, 0.75vw, 12px);
  font-weight: 600;
  padding: clamp(3px, 0.4vh, 6px) clamp(8px, 0.7vw, 12px);
  border-radius: clamp(4px, 0.4vw, 8px);
  margin-bottom: clamp(10px, 1.5vh, 18px);
  letter-spacing: 0.2px;
}

/* MAIN HEADLINE */
.title {
  font-size: clamp(18px, 1.8vw, 28px);
  font-weight: 600;
  color: #111827;
  line-height: 1.25;
  margin: 0 0 clamp(10px, 1.5vh, 18px) 0;
  letter-spacing: -0.3px;
}

/* BODY PARAGRAPH */
.description {
  font-size: clamp(11.5px, 0.85vw, 14.5px);
  line-height: 1.55;
  color: #6b7280;
  margin: 0 0 clamp(16px, 2.5vh, 32px) 0;
  font-weight: 400;
}

/* BLACK CTA BUTTON */
.contact-btn {
  background-color: #a3e635;
  color: #000000;
  border: none;
  border-radius: clamp(6px, 0.6vw, 10px);
  padding: clamp(8px, 1vh, 12px) clamp(16px, 1.3vw, 24px);
  font-size: clamp(11px, 0.8vw, 14px);
  font-weight: 600;
  cursor: pointer;
  transition: background-color 0.2s ease, transform 0.1s ease;
}

.contact-btn:hover {
  background-color: #72b605;
}

.contact-btn:active {
  transform: scale(0.98);
}

/* RESPONSIVE LAYOUT */
@media (max-width: 768px) {
  .ai-banner {
    min-height: auto;
    padding: clamp(12px, 2vh, 20px);
    background-position: center;
  }

  .content-card {
    max-width: 100%;
    padding: clamp(16px, 2.5vh, 28px);
  }
}
</style>