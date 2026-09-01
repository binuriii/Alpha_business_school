<script setup>
import { ref } from 'vue'

const scrollContainer = ref(null)
const activeIndex = ref(0)

const essentialSkillsCards = ref([
  {
    id: 1,
    title: 'ACCA',
    image: 'https://elements-resized.envatousercontent.com/envato-dam-assets-production/EVA/TRX/43/94/6d/b3/c5/v1_E11/E118XP92.jpg?w=800&cf_fit=scale-down&q=85&format=auto&s=7a4758d026b0d502377e0d5cf65beeb23117ec7a8851fa877d6cb8228e23154f',
    linkUrl: '#'
  },
  {
    id: 2,
    title: 'CFA',
    image: 'https://elements-resized.envatousercontent.com/envato-dam-assets-production/portfolio-manager/e0e5a5b2-f5e5-4863-8522-268bae8c0a68/4b8e6d86-a052-421c-9ca9-ee40c4ff84f5/DSC_5133.jpg?w=800&cf_fit=scale-down&q=85&format=auto&s=ce7ab5731c805bc6eb68edd1f99f5a1148bf8230e7d9ab6255183a775e745db6',
    linkUrl: '#'
  },
  {
    id: 3,
    title: 'CPA Australia',
    image: 'https://images.unsplash.com/photo-1759852692971-a2abc6799cbd?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8ODl8fE1vZGVzJTIwb2YlMjBTdHVkeSUyMHRvJTIwQ2hvb3NlJTIwRnJvbXxlbnwwfHwwfHx8MA%3D%3D',
  
    linkUrl: '#'
  },
  {
    id: 4,
    title: 'Financial Modeling',
    image: 'https://elements-resized.envatousercontent.com/envato-dam-assets-production/portfolio-manager/e0e5a5b2-f5e5-4863-8522-268bae8c0a68/8b19962d-e87c-4017-8002-dabcf75cfc6e/DSC_4711.jpg?w=800&cf_fit=scale-down&q=85&format=auto&s=ad50749e1a174e1bd7eb15aeab2fa724fb47016815f27fd496ee21905b06c809',
    linkUrl: '#'
  },
  {
    id: 5,
    title: 'Business Strategy',
    image: 'https://images.unsplash.com/photo-1581090698407-7d93959da202?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
    linkUrl: '#'
  }
])

const scrollToCard = (index) => {
  if (!scrollContainer.value) return
  
  if (index < 0) {
    index = essentialSkillsCards.value.length - 1
  } else if (index >= essentialSkillsCards.value.length) {
    index = 0
  }
  
  const cards = scrollContainer.value.querySelectorAll('.skills-card')
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
  scrollToCard(activeIndex.value - 1)
}

const nextSlide = () => {
  scrollToCard(activeIndex.value + 1)
}
</script>

<template>
  <section class="essential-skills-section">
    <!-- SECTION HEADER -->
    <div class="skills-header-container">
      <div class="skills-header-left">
        <h2>Build Skills That Shape Your Career</h2>
      </div>

      <div class="skills-header-right">
        <p>
          Gain globally recognized qualifications and practical skills designed to help you succeed 
          in accounting, finance, business, and beyond. Learn from experienced lecturers through 
          flexible study options at Alpha Business School.
        </p>
        <div class="skills-header-actions">
          <a href="#" class="skills-section-link">
            Explore Programs at Alpha Business School
            <svg class="skills-header-arrow" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
              <path d="M7 17L17 7M17 7H7M17 7V17"/>
            </svg>
          </a>
        </div>
      </div>
    </div>

    <!-- CAROUSEL WRAPPER WITH NAVIGATION BUTTONS -->
    <div class="skills-carousel-relative-container">
      <button class="skills-nav-arrow skills-prev-arrow" @click="prevSlide" aria-label="Previous slide">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
          <path d="M15 18l-6-6 6-6"/>
        </svg>
      </button>

      <!-- CAROUSEL TRACK -->
      <div class="skills-carousel-track" ref="scrollContainer">
        <div 
          v-for="(card, index) in essentialSkillsCards" 
          :key="card.id" 
          class="skills-card"
          @click="scrollToCard(index)"
        >
          <img :src="card.image" :alt="card.title" />
          <div class="skills-arrow-wrapper">
            <a :href="card.linkUrl" class="skills-arrow-btn" :aria-label="`Learn more about ${card.title}`">
              <span class="skills-card-title">{{ card.title }}</span>
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
                <path d="M7 17L17 7M17 7H7M17 7V17"/>
              </svg>
            </a>
          </div>
        </div>
      </div>

      <button class="skills-nav-arrow skills-next-arrow" @click="nextSlide" aria-label="Next slide">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
          <path d="M9 18l6-6-6-6"/>
        </svg>
      </button>
    </div>
  </section>
</template>

<style scoped>
/* CONTAINER STYLING WITH CLAMP & VW/VH */
.essential-skills-section {
  width: 100vw;
  max-width: 100%;
  background: #f5f4f0;
  border-radius: clamp(8px, 1.2vw, 16px);
  padding: 5% 3% 5% 3%;
  margin-top: clamp(12px, 2vh, 24px);
  box-sizing: border-box;
  overflow: hidden;
  font-family: 'Oakes Grotesk', 'Urbanist', -apple-system, BlinkMacSystemFont, sans-serif;
}

/* HEADER STYLES */
.skills-header-container {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: clamp(20px, 3.5vw, 48px);
  margin-bottom: clamp(24px, 4.5vh, 56px);
}

.skills-header-left {
  flex: 1;
}

.skills-header-left h2 {
  margin: 0;
  font-size: clamp(22px, 2.2vw, 36px);
  font-weight: 600;
  color: #0f172a;
  line-height: 1.2;
  font-family: inherit;
}

.skills-header-right {
  flex: 1;
}

.skills-header-right p {
  margin: 0 0 clamp(12px, 1.8vh, 24px) 0;
  font-size: clamp(12px, 0.9vw, 15px);
  line-height: 1.5;
  color: #64748b;
  font-family: inherit;
}

.skills-header-actions {
  display: flex;
  align-items: center;
}

.skills-section-link {
  display: inline-flex;
  align-items: center;
  gap: clamp(4px, 0.5vw, 8px);
  font-size: clamp(12px, 0.9vw, 15px);
  font-weight: 700;
  color: #0f172a;
  text-decoration: none;
  transition: opacity 0.2s ease;
  font-family: inherit;
}

.skills-section-link:hover {
  opacity: 0.75;
}

.skills-header-arrow {
  width: clamp(12px, 1vw, 16px);
  height: clamp(12px, 1vw, 16px);
}

/* CAROUSEL RELATIVE WRAPPER */
.skills-carousel-relative-container {
  position: relative;
  width: 100%;
}

/* CAROUSEL TRACK & CARDS */
.skills-carousel-track {
  display: flex;
  gap: clamp(12px, 1.5vw, 24px);
  overflow-x: auto;
  scroll-behavior: smooth;
  scrollbar-width: none;
  padding-bottom: clamp(6px, 1vh, 12px);
}

.skills-carousel-track::-webkit-scrollbar {
  display: none;
}

.skills-card {
  position: relative;
  flex: 0 0 calc(25% - clamp(9px, 1.2vw, 18px));
  min-width: clamp(200px, 18vw, 260px);
  height: clamp(300px, 42vh, 420px);
  border-radius: clamp(12px, 1.5vw, 20px);
  overflow: hidden;
  cursor: pointer;
  transition: transform 0.3s ease;
}

.skills-card:hover {
  transform: translateY(-0.5vh);
}

.skills-card img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

/* CORNER LINK NOTCH EFFECT WITH COURSE TITLE */
.skills-arrow-wrapper {
  position: absolute;
  bottom: 0;
  left: 0;
  right: clamp(12px, 1.5vw, 24px);
  background: #0a0a0a;
  padding: clamp(8px, 1vh, 14px) clamp(10px, 1vw, 16px);
  border-top-right-radius: clamp(16px, 1.8vw, 26px);
}

.skills-arrow-btn {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: clamp(6px, 0.8vw, 12px);
  text-decoration: none;
  background: transparent;
  padding: clamp(3px, 0.4vw, 6px);
  transition: transform 0.2s ease;
}

.skills-arrow-btn:hover {
  transform: translate(2px, -2px);
}

.skills-card-title {
  font-size: clamp(12px, 1vw, 14px);
  font-weight: 600;
  color: #ffffff;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  font-family: inherit;
}

.skills-arrow-btn svg {
  width: clamp(16px, 1.3vw, 15px);
  height: clamp(16px, 1.3vw, 22px);
  stroke: #fefeff;
  flex-shrink: 0;
}

/* NAVIGATION ARROWS */
.skills-nav-arrow {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: clamp(28px, 2.4vw, 40px);
  height: clamp(28px, 2.4vw, 40px);
  border-radius: 50%;
  background: #ffffff;
  border: 1px solid #cbd5e1;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 10;
  box-shadow: 0 4px 10px rgba(15, 23, 42, 0.08);
  transition: all 0.2s ease;
}

.skills-nav-arrow:hover {
  border-color: #0f172a;
  background-color: #f1f5f9;
}

.skills-nav-arrow svg {
  width: clamp(12px, 1vw, 18px);
  height: clamp(12px, 1vw, 18px);
  stroke: #0f172a;
}

.skills-prev-arrow {
  left: clamp(-16px, -1vw, -10px);
}

.skills-next-arrow {
  right: clamp(-16px, -1vw, -10px);
}

/* RESPONSIVE BREAKPOINTS */
@media (max-width: 900px) {
  .skills-header-container {
    flex-direction: column;
    gap: clamp(12px, 1.8vh, 20px);
  }
  .skills-card {
    flex: 0 0 calc(40% - clamp(6px, 1vw, 12px));
    height: clamp(260px, 35vh, 340px);
  }
}

@media (max-width: 640px) {
  .skills-card {
    flex: 0 0 80vw;
  }
  .skills-nav-arrow {
    display: none;
  }
}
</style>