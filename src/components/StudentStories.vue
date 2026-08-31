<script setup>
import { ref } from 'vue'

const currentIndex = ref(1) // Default active slide (0-based: 2 = Nethmi)

const stories = ref([
  {
    id: 1,
    quote: 'The structured guidance and mock exams gave me the exact confidence I needed to pass my papers on the very first attempt.',
    author: 'Kavinda',
    program: 'ACCA student',
    image: 'https://images.unsplash.com/photo-1580489944761-15a19d654956?q=80&w=1361&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
  },
  {
    id: 2,
    quote: 'Flexibility between live online lectures and recorded sessions allowed me to balance a demanding full-time job while preparing for my exams.',
    author: 'Dilini',
    program: 'CFA candidate',
    image: 'https://images.unsplash.com/photo-1573496359142-b8d87734a5a2?q=80&w=800&auto=format&fit=crop'
  },
  {
    id: 3,
    quote: 'One-to-one support from the lecturers meant I never fell behind, even during the busiest audit season at work.',
    author: 'Nethmi',
    program: 'CPA Australia student',
    image: 'https://images.unsplash.com/photo-1580489944761-15a19d654956?q=80&w=1361&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
  },
  {
    id: 4,
    quote: 'The practical financial modeling skills I learned here directly helped me land my dream role in investment banking.',
    author: 'Thejan',
    program: 'AFM student',
    image: 'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?q=80&w=800&auto=format&fit=crop'
  }
])

const nextSlide = () => {
  if (currentIndex.value < stories.value.length - 1) {
    currentIndex.value++
  } else {
    currentIndex.value = 0
  }
}

const prevSlide = () => {
  if (currentIndex.value > 0) {
    currentIndex.value--
  } else {
    currentIndex.value = stories.value.length - 1
  }
}

const goToSlide = (index) => {
  currentIndex.value = index
}
</script>

<template>
  <section class="student-stories-section">
    <!-- TOP CENTER HEADER -->
    <div class="top-header">
      <h2>What passing <em>actually sounds like.</em></h2>
    </div>

    <!-- MAIN TWO-COLUMN CONTENT AREA -->
    <div class="main-content">
      <!-- LEFT SIDEBAR CONTROL PANEL -->
      <div class="sidebar-panel">
        <div class="quote-icon">“</div>
        <h3 class="sidebar-title">What passing <em>actually sounds like.</em></h3>

        <!-- NAV CONTROLS WITH PROGRESS INDICATORS -->
        <div class="nav-controls-row">
          <button 
            class="nav-btn" 
            @click="prevSlide" 
            aria-label="Previous story"
          >
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M15 18l-6-6 6-6"/>
            </svg>
          </button>

          <div class="indicators">
            <span 
              v-for="(story, index) in stories" 
              :key="story.id"
              class="dot"
              :class="{ active: index === currentIndex }"
              @click="goToSlide(index)"
            ></span>
          </div>

          <button 
            class="nav-btn" 
            @click="nextSlide" 
            aria-label="Next story"
          >
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <path d="M9 18l6-6-6-6"/>
            </svg>
          </button>
        </div>
      </div>

      <!-- RIGHT SIDE CAROUSEL SLIDER -->
      <div class="cards-carousel">
        <div 
          class="cards-track" 
          :style="{ transform: `translateX(-${currentIndex * 320}px)` }"
        >
          <div 
            v-for="(story, index) in stories" 
            :key="story.id"
            class="testimonial-card"
            :class="{ active: index === currentIndex }"
          >
            <p class="quote-text">{{ story.quote }}</p>

            <div class="rating-stars">
              <span v-for="star in 5" :key="star" class="star">★</span>
            </div>

            <div class="author-row">
              <div class="profile-circle">
                <img :src="story.image" :alt="story.author" />
              </div>
              <div class="author-details">
                <strong class="author-name">{{ story.author }}</strong>
                <span class="program-name">{{ story.program }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
/* CONTAINER STYLING WITH CLAMP & VW/VH (FROM REFERENCE FILE) */
.student-stories-section {
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

/* TOP CENTER HEADER TYPOGRAPHY */
.top-header {
  text-align: center;
  margin-bottom: clamp(24px, 4.5vh, 48px);
}

.top-header h2 {
  margin: 0;
  font-size: clamp(22px, 2.2vw, 36px);
  font-weight: 600;
  color: #0f172a;
  line-height: 1.2;
  font-family: inherit;
}

.top-header h2 em,
.sidebar-title em {
  font-style: italic;
  font-weight: 400;
}

/* MAIN CONTENT GRID */
.main-content {
  max-width: 1240px;
  margin: 0 auto;
  display: flex;
  align-items: center;
  gap: clamp(20px, 3.5vw, 48px);
}

/* LEFT SIDEBAR PANEL */
.sidebar-panel {
  flex: 0 0 clamp(220px, 22vw, 300px);
  display: flex;
  flex-direction: column;
}

.quote-icon {
  font-size: clamp(48px, 5vw, 80px);
  line-height: 0.6;
  color: #cbd5e1;
  font-family: Georgia, serif;
}

.sidebar-title {
  margin: clamp(10px, 1.5vh, 18px) 0 clamp(16px, 2vh, 28px) 0;
  font-size: clamp(18px, 1.6vw, 24px);
  font-weight: 600;
  color: #0f172a;
  line-height: 1.3;
  font-family: inherit;
}

/* CAROUSEL CONTROLS & INDICATORS */
.nav-controls-row {
  display: flex;
  align-items: center;
  gap: clamp(12px, 1.2vw, 20px);
}

.nav-btn {
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
  padding: 0;
}

.nav-btn:hover {
  border-color: #0f172a;
  background-color: #f1f5f9;
}

.nav-btn svg {
  width: clamp(12px, 1.2vw, 18px);
  height: clamp(12px, 1.2vw, 18px);
  stroke: #0f172a;
}

.indicators {
  display: flex;
  align-items: center;
  gap: clamp(6px, 0.6vw, 10px);
}

.dot {
  width: clamp(6px, 0.6vw, 10px);
  height: clamp(6px, 0.6vw, 10px);
  border-radius: 50%;
  background-color: #cbd5e1;
  cursor: pointer;
  transition: all 0.3s ease;
}

.dot.active {
  width: clamp(18px, 1.8vw, 28px);
  border-radius: clamp(3px, 0.3vw, 5px);
  background-color: #0f172a;
}

/* RIGHT CAROUSEL TRACK */
.cards-carousel {
  flex: 1;
  overflow: hidden;
  padding: clamp(4px, 0.5vh, 8px) 0 clamp(8px, 1vh, 16px) 0;
  min-width: 0;
}

.cards-track {
  display: flex;
  gap: clamp(12px, 1.5vw, 24px);
  transition: transform 0.4s cubic-bezier(0.25, 1, 0.5, 1);
}

/* TESTIMONIAL CARDS */
.testimonial-card {
  flex: 0 0 clamp(260px, 22vw, 310px);
  background: #ffffff;
  border: 1px solid #f1f5f9;
  border-radius: clamp(12px, 1.5vw, 20px);
  padding: clamp(16px, 2vh, 24px);
  box-shadow: 0 4px 12px rgba(15, 23, 42, 0.05);
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  box-sizing: border-box;
}

.quote-text {
  font-size: clamp(12px, 0.9vw, 15px);
  line-height: 1.5;
  color: #64748b;
  margin: 0 0 clamp(12px, 1.5vh, 20px) 0;
  font-family: inherit;
  display: -webkit-box;
  -webkit-line-clamp: 5;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.rating-stars {
  color: #0f172a;
  font-size: clamp(12px, 0.9vw, 14px);
  letter-spacing: 2px;
  margin-bottom: clamp(12px, 1.5vh, 20px);
}

.author-row {
  display: flex;
  align-items: center;
  gap: clamp(8px, 1vw, 14px);
}

.profile-circle {
  width: clamp(32px, 2.5vw, 42px);
  height: clamp(32px, 2.5vw, 42px);
  border-radius: 50%;
  overflow: hidden;
  flex-shrink: 0;
}

.profile-circle img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.author-details {
  display: flex;
  flex-direction: column;
}

.author-name {
  font-size: clamp(13px, 1.1vw, 15px);
  font-weight: 600;
  color: #0f172a;
  font-family: inherit;
}

.program-name {
  font-size: clamp(11px, 0.8vw, 13px);
  color: #64748b;
  font-family: inherit;
}

/* RESPONSIVE BREAKPOINTS (MATCHING REFERENCE) */
@media (max-width: 900px) {
  .main-content {
    flex-direction: column;
    align-items: flex-start;
  }

  .sidebar-panel {
    flex: 0 0 auto;
    width: 100%;
  }

  .cards-carousel {
    width: 100%;
  }
}
</style>