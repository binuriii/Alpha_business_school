<script setup>
const cards = [
  {
    type: 'light',
    tag: 'WHO WE ARE',
    title: 'A Leading Business Education Institution in Sri Lanka',
    image: 'https://images.unsplash.com/photo-1522071820081-009f0129c71c?q=80&w=1200&auto=format&fit=crop',
    imageAlt: 'Team working on laptop'
  },
  {
    type: 'highlight',
    tag: 'OUR ADVANTAGE',
    title: 'Sri Lanka’s Largest Portfolio of Global Qualifications',
    image: highlightCardBg,
    imageAlt: 'Team collaborating around laptop'
  },
  {
    type: 'light',
    tag: 'YOUR FUTURE',
    title: 'Qualifications That Open Doors to Global Careers',
    image: 'https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?q=80&w=1200&auto=format&fit=crop',
    imageAlt: 'Professional woman holding tablet'
  }
]
</script>

<template>
  <section class="cards-section">
    <div class="cards-grid">
      <template v-for="(card, index) in cards" :key="index">
        <!-- SECOND CARD (PRE-MASKED LIME GRAPHIC CARD) -->
        <div 
          v-if="card.type === 'highlight'" 
          class="card highlight-card"
          :style="{ backgroundImage: `url(${card.image})` }"
        >
          <div class="highlight-content">
            <span class="card-tag tag-dark-outline">{{ card.tag }}</span>
            <div class="footer-bottom">
              <h3 class="card-title title-dark">{{ card.title }}</h3>
              <button class="arrow-btn btn-white" aria-label="Open article">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
                  <path d="M7 17L17 7M17 7H7M17 7V17"/>
                </svg>
              </button>
            </div>
          </div>
        </div>

        <!-- FIRST AND THIRD CARDS (LIGHT CARDS) -->
        <div v-else class="card light-card">
          <div class="card-header">
            <div class="header-top">
              <span class="card-tag tag-gray">{{ card.tag }}</span>
              <button class="arrow-btn btn-outline" aria-label="Open article">
                <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
                  <path d="M7 17L17 7M17 7H7M17 7V17"/>
                </svg>
              </button>
            </div>
            <h3 class="card-title title-dark-green">{{ card.title }}</h3>
          </div>

          <div class="card-image-box">
            <img :src="card.image" :alt="card.imageAlt" />
          </div>
        </div>
      </template>
    </div>
  </section>
</template>

<style scoped>
.cards-section {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 5% 3% 5% 3%;
  margin-top: clamp(12px, 2vh, 24px);
  box-sizing: border-box;
  font-family: 'Oakes Grotesk', 'Urbanist', -apple-system, BlinkMacSystemFont, sans-serif;
}

.cards-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

/* BASE CARD */
.card {
  border-radius: 28px;
  overflow: hidden;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 480px;
  padding: 24px;
  box-sizing: border-box;
  position: relative;
}

/* LIGHT CARD STYLING */
.light-card {
  background-color: #f5f4f0;
}

.card-header {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.header-top {
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.card-tag {
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.5px;
  padding: 6px 14px;
  border-radius: 20px;
  display: inline-block;
  text-transform: uppercase;
}

.tag-gray {
  background: transparent;
  border: 1px solid #e2e0d8;
  color: #475569;
}

.tag-dark-outline {
  background: transparent;
  border: 1px solid rgba(15, 23, 42, 0.2);
  color: #0f172a;
  width: fit-content;
}

.card-title {
  font-size: 20px;
  font-weight: 600;
  line-height: 1.35;
  margin: 0;
  letter-spacing: -0.3px;
}

.title-dark-green {
  color: #1e3a34;
}

.title-dark {
  color: #0f172a;
}

.card-image-box {
  width: 100%;
  height: 250px;
  border-radius: 20px;
  overflow: hidden;
  margin-top: 24px;
}

.card-image-box img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* HIGHLIGHT CARD (USING FULL-SIZE GRAPHIC) */
.highlight-card {
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  justify-content: flex-end;
}

.highlight-content {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.footer-bottom {
  display: flex;
  align-items: flex-end;
  justify-content: space-between;
  gap: 16px;
}

/* BUTTONS */
.arrow-btn {
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  flex-shrink: 0;
  border: none;
  transition: transform 0.2s ease;
}

.arrow-btn:hover {
  transform: scale(1.05);
}

.arrow-btn svg {
  width: 16px;
  height: 16px;
}

.btn-outline {
  background: #ffffff;
  color: #0f172a;
  box-shadow: 0 2px 8px rgba(0,0,0,0.04);
}

.btn-white {
  background: #ffffff;
  color: #0f172a;
}

/* RESPONSIVE */
@media (max-width: 960px) {
  .cards-grid {
    grid-template-columns: 1fr;
  }
}
</style>