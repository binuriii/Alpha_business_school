<script setup>
import { ref } from 'vue'

const scrollContainer = ref(null)
const activeIndex = ref(0)

const whyAlphaCards = ref([
  {
    id: 1,
    title: 'World Class Lecturers',
    image: 'https://elements-resized.envatousercontent.com/envato-dam-assets-production/EVA/TRX/7b/1e/94/0d/01/v1_E10/E106HIVT.JPG?w=800&cf_fit=scale-down&q=85&format=auto&s=96f610dc615e2112a640f742a5fed294ca2808adec5789f7a8a6b654c1fe6656',
    linkUrl: '#'
  },
  {
    id: 2,
    title: 'Modes of Study to Choose From',
    image: 'https://images.unsplash.com/photo-1765020553499-1ec9aeb21298?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDg2fHx8ZW58MHx8fHx8',
    linkUrl: '#'
  },
  {
    id: 3,
    title: 'Excellent Pass Rates',
    image: 'https://images.unsplash.com/photo-1555725305-e823b44548de?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDN8fHxlbnwwfHx8fHw%3D',
    linkUrl: '#'
  },  
  {
    id: 4,
    title: 'Comprehensive Material',
    image: 'https://elements-resized.envatousercontent.com/envato-dam-assets-production/1da902e5-8bb7-4bc2-883f-e253ca487511/1ad7916d-dae8-41c7-9919-32776a57c909.jpg?w=800&cf_fit=scale-down&q=85&format=auto&s=d68acb5096c216f68dfd17406d1aff15be15f4d96fdba03d1f5880b867431f32',
    linkUrl: '#'
  },
  {
    id: 5,
    title: 'Recordings at Your Convenience',
    image: 'https://plus.unsplash.com/premium_photo-1683887034552-4635692bb57c?q=80&w=2069&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
    linkUrl: '#'
  },
])

const scrollToCard = (index) => {
  if (!scrollContainer.value) return
  const cards = scrollContainer.value.querySelectorAll('.why-alpha-card')
  if (cards[index]) {
    cards[index].scrollIntoView({
      behavior: 'smooth',
      inline: 'start',
      block: 'nearest'
    })
    activeIndex.value = index
  }
}

const prevSlide = () => {
  if (activeIndex.value > 0) {
    scrollToCard(activeIndex.value - 1)
  } else {
    scrollToCard(whyAlphaCards.value.length - 1)
  }
}

const nextSlide = () => {
  if (activeIndex.value < whyAlphaCards.value.length - 1) {
    scrollToCard(activeIndex.value + 1)
  } else {
    scrollToCard(0)
  }
}
</script>

<template>
  <section class="why-alpha-section">
    <div class="why-alpha-container">
      <!-- LEFT TEXT COLUMN WITH CONTROLS BELOW PARAGRAPH -->
      <div class="why-alpha-header">
        <h2>Why <em>Alpha Business School ?</em></h2>
        <p>
          Discover a vibrant campus experience filled with opportunities to connect, grow and thrive. 
          From clubs and sports to events and friendships, student life at Alpha Business School is dynamic and inclusive.
        </p>

        <!-- CAROUSEL CONTROLS MOVED UNDER PARAGRAPH -->
        <div class="why-alpha-carousel-controls">
          <button class="why-alpha-nav-btn" @click="prevSlide" aria-label="Previous slide">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M15 18l-6-6 6-6"/>
            </svg>
          </button>

          <div class="why-alpha-indicators">
            <span 
              v-for="(card, index) in whyAlphaCards" 
              :key="index"
              class="why-alpha-dot"
              :class="{ active: index === activeIndex }"
              @click="scrollToCard(index)"
            ></span>
          </div>

          <button class="why-alpha-nav-btn" @click="nextSlide" aria-label="Next slide">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M9 18l6-6-6-6"/>
            </svg>
          </button>
        </div>
      </div>

      <!-- RIGHT CAROUSEL COLUMN -->
      <div class="why-alpha-carousel-wrapper">
        <div class="why-alpha-carousel-track" ref="scrollContainer">
          <div 
            v-for="card in whyAlphaCards" 
            :key="card.id" 
            class="why-alpha-card"
          >
            <div class="why-alpha-card-image-wrap">
              <img :src="card.image" :alt="card.title" />
            </div>

            <!-- FLOATING TITLE BADGE WITH 45° ARROW -->
            <a :href="card.linkUrl" class="why-alpha-card-badge">
              <span class="why-alpha-badge-title">{{ card.title }}</span>
              <svg class="why-alpha-badge-arrow" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
                <path d="M7 17L17 7M17 7H7M17 7V17"/>
              </svg>
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* CONTAINER STYLING WITH CLAMP & VW/VH */
.why-alpha-section {
  width: 100vw;
  max-width: 100%;
  background: #ffffff;
  border-radius: clamp(8px, 1.2vw, 16px);
  padding: 5% 3% 5% 3%;
  margin-top: clamp(12px, 2vh, 24px);
  box-sizing: border-box;
  overflow: hidden;
  font-family: 'Oakes Grotesk', 'Urbanist', -apple-system, BlinkMacSystemFont, sans-serif;
}

.why-alpha-container {
  max-width: 1240px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  gap: clamp(20px, 3.5vw, 48px);
}

/* LEFT COLUMN STYLES */
.why-alpha-header {
  flex: 0 0 clamp(220px, 22vw, 300px);
  display: flex;
  flex-direction: column;
}

.why-alpha-header h2 {
  margin: 0 0 clamp(10px, 1.5vh, 18px) 0;
  font-size: clamp(22px, 2.2vw, 36px);
  font-weight: 600;
  color: #0f172a;
  line-height: 1.2;
  font-family: inherit;
}

.why-alpha-header h2 em {
  font-style: italic;
  font-weight: 400;
}

.why-alpha-header p {
  margin: 0;
  font-size: clamp(12px, 0.9vw, 15px);
  line-height: 1.5;
  color: #64748b;
  font-family: inherit;
}

/* CAROUSEL WRAPPER & TRACK */
.why-alpha-carousel-wrapper {
  flex: 1;
  display: flex;
  flex-direction: column;
  min-width: 0;
}

.why-alpha-carousel-track {
  display: flex;
  gap: clamp(12px, 1.5vw, 24px);
  overflow-x: auto;
  scroll-behavior: smooth;
  scrollbar-width: none;
  padding: clamp(4px, 0.5vh, 8px) 0 clamp(8px, 1vh, 16px) 0;
}

.why-alpha-carousel-track::-webkit-scrollbar {
  display: none;
}

.why-alpha-card {
  position: relative;
  flex: 0 0 calc(33.333% - clamp(8px, 1vw, 16px));
  min-width: clamp(220px, 20vw, 280px);
  height: clamp(300px, 42vh, 420px);
  border-radius: clamp(12px, 1.5vw, 20px);
  overflow: hidden;
  transition: transform 0.3s ease;
}

.why-alpha-card:hover {
  transform: translateY(-0.5vh);
}

.why-alpha-card-image-wrap {
  width: 100%;
  height: 100%;
}

.why-alpha-card-image-wrap img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* FLOATING WHITE BADGE WITH CLAMP PADDING & FONT SIZES */
.why-alpha-card-badge {
  position: absolute;
  bottom: clamp(10px, 1.5vh, 20px);
  left: clamp(10px, 1.2vw, 18px);
  right: clamp(10px, 1.2vw, 18px);
  background: #000000;
  border-radius: clamp(8px, 1vw, 14px);
  padding: clamp(10px, 1.2vh, 16px) clamp(12px, 1.2vw, 20px);
  display: flex;
  align-items: center;
  justify-content: space-between;
  text-decoration: none;
  box-shadow: 0 4px 12px rgba(15, 23, 42, 0.08);
  transition: opacity 0.2s ease;
}

.why-alpha-card-badge:hover {
  opacity: 0.9;
}

.why-alpha-badge-title {
  font-size: clamp(13px, 1.1vw, 15px);
  font-weight: 600;
  color: #ffffff;
  font-family: inherit;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.why-alpha-badge-arrow {
  width: clamp(14px, 1.2vw, 20px);
  height: clamp(14px, 1.2vw, 20px);
  stroke: #0f172a;
  flex-shrink: 0;
}

/* CONTROLS & INDICATORS POSITIONED IN LEFT COLUMN */
.why-alpha-carousel-controls {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  gap: clamp(12px, 1.2vw, 20px);
  margin-top: clamp(16px, 2.5vh, 28px);
}

.why-alpha-nav-btn {
  width: clamp(28px, 2.5vw, 36px);
  height: clamp(28px, 2.5vw, 36px);
  border-radius: 50%;
  border: 1px solid #cbd5e1;
  background: #ffffff;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.2s ease;
}

.why-alpha-nav-btn:hover {
  border-color: #0f172a;
  background-color: #f1f5f9;
}

.why-alpha-nav-btn svg {
  width: clamp(12px, 1.2vw, 18px);
  height: clamp(12px, 1.2vw, 18px);
  stroke: #0f172a;
}

.why-alpha-indicators {
  display: flex;
  align-items: center;
  gap: clamp(6px, 0.6vw, 10px);
}

.why-alpha-dot {
  width: clamp(6px, 0.6vw, 10px);
  height: clamp(6px, 0.6vw, 10px);
  border-radius: 50%;
  background-color: #cbd5e1;
  cursor: pointer;
  transition: all 0.3s ease;
}

.why-alpha-dot.active {
  width: clamp(18px, 1.8vw, 28px);
  border-radius: clamp(3px, 0.3vw, 5px);
  background-color: #0f172a;
}

/* RESPONSIVE BREAKPOINTS */
@media (max-width: 900px) {
  .why-alpha-container {
    flex-direction: column;
    align-items: flex-start;
  }

  .why-alpha-header {
    flex: 0 0 auto;
    max-width: 100%;
  }

  .why-alpha-carousel-wrapper {
    width: 100%;
  }

  .why-alpha-card {
    flex: 0 0 calc(50% - clamp(6px, 1vw, 12px));
    height: clamp(260px, 35vh, 340px);
  }
}

@media (max-width: 640px) {
  .why-alpha-card {
    flex: 0 0 85vw;
  }
}
</style>