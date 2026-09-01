<script setup>
import { ref, computed } from 'vue'

const activeIndex = ref(1)

const milestones = [
  {
    year: '1859',
    title: 'Foundation of Academic Excellence',
    description: 'The institution laid its groundwork as a pioneer in specialized training and higher legal education.',
    image: 'https://images.unsplash.com/photo-1562774053-701939374585?q=80&w=2372&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
  },
  {
    year: '1972',
    title: 'The Alpha Business School is established',
    description: 'Created by an Act of the Victorian Parliament, the Leo Cussen Institute was founded as a not-for-profit statutory body dedicated to practical legal education and professional development.',
    image: 'https://images.unsplash.com/photo-1762245955112-b3170b131b0d?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDV8fHxlbnwwfHx8fHw%3D'
  },
  {
    year: '2010',
    title: 'Expansion into Digital & Online Learning',
    description: 'Introducing adaptive online classrooms and virtual simulated learning environments for students nationwide.',
    image: 'https://images.unsplash.com/photo-1665780993894-ceb3a89bc5c5?q=80&w=2070&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
  },
  {
    year: '2026',
    title: 'Leading Modern Technological Integration',
    description: 'Empowering future leaders through advanced AI-assisted coursework, smart campus infrastructure, and global partnerships.',
    image: 'https://images.unsplash.com/photo-1741707596991-89e3d5dc6735?q=80&w=2071&auto=format&fit=crop&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D'
  }
]

const activeMilestone = computed(() => milestones[activeIndex.value])

const prevMilestone = () => {
  if (activeIndex.value > 0) activeIndex.value--
}

const nextMilestone = () => {
  if (activeIndex.value < milestones.length - 1) activeIndex.value++
}
</script>

<template>
  <section class="legacy-section">
    <!-- HERO TITLE & THREE-COLUMN INTRO SECTION -->
    <div class="champions-header">
      <div class="header-main-title">
        <h2>Empowering Your<br />Career Journey</h2>
      </div>
      <div class="header-desc-col">
        <p>
          At Alpha Business School, we prepare students for the demands of today’s global business world through internationally recognized qualifications in accounting, finance, business, risk, and financial modeling.
        </p>
      </div>
      <div class="header-action-col">
        <p>
          Learn from experienced industry professionals through physical, online, blended, and on-demand classes — with practical knowledge and dedicated support designed to help you succeed.
        </p>
        <a href="#" class="book-lesson-btn">
          Explore Our Programs
          <span class="btn-arrow-box">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
              <path d="M9 5l7 7-7 7" />
            </svg>
          </span>
        </a>
      </div>
    </div>

    <!-- MAIN EXCELLENCE DISPLAY GRID -->
    <div class="champions-grid">
      <!-- LEFT LARGE IMAGE CARD WITH OVERLAY FOOTER -->
      <div class="large-hero-card">
        <img src="https://elements-resized.envatousercontent.com/envato-dam-assets-production/portfolio-manager/e0e5a5b2-f5e5-4863-8522-268bae8c0a68/3e8cc3c3-f04d-4b18-a08f-c2af0966e216/DSC_4976.jpg?w=1600&cf_fit=scale-down&q=85&format=auto&s=fd0647d3002cc309389ba22db7b24c7103567a665590fddff484ac75dbcc07bd" alt="Tennis player holding racket" />
        <div class="card-overlay-footer">
          <div class="overlay-stat">
            <span class="stat-value">25+</span>
            <span class="stat-name">Globally
Recognized Qualifications</span>
          </div>
          <div class="overlay-stat">
            <span class="stat-value">20+</span>
            <span class="stat-name">Experienced
Industry Lecturers</span>
          </div>
          <a href="#" class="overlay-action-btn" aria-label="Learn more">
            <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
              <path d="M7 17L17 7M17 7H7M17 7V17" />
            </svg>
          </a>
        </div>
      </div>

      <!-- RIGHT SIDE: SMALL IMAGE + STAT BLOCK -->
      <div class="champions-right-col">
        <div class="small-image-card">
          <img src="https://elements-resized.envatousercontent.com/envato-dam-assets-production/portfolio-manager/e0e5a5b2-f5e5-4863-8522-268bae8c0a68/22f8955b-7da0-4e15-bd8c-f7027a2561ec/DSC_4085.jpg?w=800&cf_fit=scale-down&q=85&format=auto&s=49940a783f923b0272e275b0cb27f4d1272e25c28b4fcf5a7a14e33920e942d5" alt="Female tennis player on court" />
        </div>

        <div class="excellence-stats-block">
          <div class="years-display">
            <span class="big-number">15</span>
            <span class="big-number-label">Years of<br />Excellence</span>
          </div>

          <ul class="features-list">
            <li>Experienced & qualified lecturers</li>
            <li>Flexible learning options</li>
            <li>Practical, career-focused education</li>
          </ul>
        </div>
      </div>
    </div>

    <!-- DIVIDER -->
    <hr class="section-divider" />

    <!-- STANDARDIZED HEADER LAYOUT -->
    <div class="header-container">
      <div class="header-left">
        <h2>Trusted for more than<br />50 years</h2>
      </div>
      <div class="header-right">
        <p>
          Explore the key milestones that have shaped Leo Cussen's evolution into one of Australia's leading providers of practical legal education and professional development.
        </p>
      </div>
    </div>

    <!-- TIMELINE CONTROLS -->
    <div class="timeline-wrapper">
      <button 
        class="nav-arrow" 
        @click="prevMilestone" 
        :disabled="activeIndex === 0"
        aria-label="Previous Milestone"
      >
        ←
      </button>

      <div class="timeline-track">
        <div 
          class="timeline-progress" 
          :style="{ width: `${(activeIndex / (milestones.length - 1)) * 100}%` }"
        ></div>
        
        <div 
          v-for="(item, index) in milestones" 
          :key="item.year"
          class="timeline-node"
          :class="{ active: index === activeIndex, past: index < activeIndex }"
          @click="activeIndex = index"
        >
          <span class="node-year">{{ item.year }}</span>
          <div class="node-dot"></div>
        </div>
      </div>

      <button 
        class="nav-arrow" 
        @click="nextMilestone" 
        :disabled="activeIndex === milestones.length - 1"
        aria-label="Next Milestone"
      >
        →
      </button>
    </div>

    <!-- ACTIVE CONTENT -->
    <div class="milestone-content">
      <div class="milestone-text">
        <h1 class="active-year">{{ activeMilestone.year }}</h1>
        <h3>{{ activeMilestone.title }}</h3>
        <p>{{ activeMilestone.description }}</p>
      </div>

      <div class="milestone-image">
        <img :src="activeMilestone.image" :alt="activeMilestone.title" />
      </div>
    </div>

  </section>
</template>

<style scoped>
/* CONTAINER STYLING */
* {
  font-family: 'Oakes Grotesk', 'Urbanist', -apple-system, BlinkMacSystemFont, sans-serif;
}

.legacy-section {
  width: 100vw;
  max-width: 100%;
  background: #ffffff;
  border-radius: clamp(8px, 1.2vw, 16px);
  padding: 5% 4%;
  margin-top: clamp(12px, 2vh, 24px);
  box-sizing: border-box;
}

/* CHAMPIONS HEADER LAYOUT */
.champions-header {
  display: grid;
  grid-template-columns: 1.2fr 1fr 1fr;
  gap: clamp(20px, 3vw, 40px);
  align-items: start;
  margin-bottom: clamp(28px, 4vh, 48px);
}

.header-main-title h2 {
  font-size: clamp(26px, 2.8vw, 42px);
  font-weight: 500;
  color: #0f172a;
  line-height: 1.05;
  margin: 0;
  letter-spacing: -0.02em;
}

.header-desc-col p,
.header-action-col p {
  font-size: clamp(12px, 0.85vw, 14px);
  line-height: 1.5;
  color: #64748b;
  margin: 0 0 16px 0;
}

.book-lesson-btn {
  display: inline-flex;
  align-items: center;
  background: #000000;
  color: #ffffff;
  font-weight: 600;
  font-size: clamp(12px, 0.85vw, 14px);
  text-decoration: none;
  padding: 4px 4px 4px 16px;
  border-radius: 24px;
  gap: 12px;
  transition: opacity 0.2s ease;
}

.book-lesson-btn:hover {
  opacity: 0.9;
}

.btn-arrow-box {
  background: #a3e635;
  width: 28px;
  height: 28px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 100px;
}

.btn-arrow-box svg {
  width: 14px;
  height: 14px;
  stroke: #0f172a;
}

/* CHAMPIONS DISPLAY GRID */
.champions-grid {
  display: grid;
  grid-template-columns: 1.8fr 1fr;
  gap: clamp(20px, 3vw, 40px);
  align-items: stretch;
}

/* LARGE HERO CARD WITH FULL-BLEED FILL */
.large-hero-card {
  position: relative;
  border-radius: 12px;
  overflow: hidden;
  height: clamp(450px, 60vh, 620px);
  background: #a3e635;
}

/* Pattern image */
.large-hero-card img {
  position: absolute;
  width: 110%;
  height: 100%;
  max-width: none;
  object-fit: cover;
  object-position: center;
  display: block;
}

.card-overlay-footer {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background: linear-gradient(180deg, rgba(15, 23, 42, 0) 0%, rgba(15, 23, 42, 0.85) 100%);
  display: flex;
  align-items: flex-end;
  padding: 24px;
  gap: 16px;
  z-index: 2;
}

.overlay-stat {
  background: rgba(15, 23, 42, 0.4);
  backdrop-filter: blur(8px);
  padding: 12px 16px;
  border-radius: 6px;
  min-width: 110px;
}

.stat-value {
  display: block;
  font-size: clamp(20px, 1.8vw, 26px);
  font-weight: 800;
  color: #a3e635;
  line-height: 1;
}

.stat-name {
  font-size: clamp(10px, 0.75vw, 12px);
  color: #ffffff;
  opacity: 0.9;
}

.overlay-action-btn {
  margin-left: auto;
  width: 44px;
  height: 44px;
  background: rgba(255, 255, 255, 0.2);
  backdrop-filter: blur(8px);
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 6px;
  transition: background 0.2s ease;
}

.overlay-action-btn:hover {
  background: rgba(255, 255, 255, 0.35);
}

.overlay-action-btn svg {
  width: 20px;
  height: 20px;
  stroke: #ffffff;
}

/* RIGHT COLUMN STYLING */
.champions-right-col {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  gap: clamp(20px, 2.5vh, 32px);
}

.small-image-card {
  height: clamp(180px, 24vh, 250px);
  border-radius: 8px;
  overflow: hidden;
}

.small-image-card img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.excellence-stats-block {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.years-display {
  display: flex;
  align-items: center;
  gap: 16px;
}

.big-number {
  font-size: clamp(150px, 6vw, 96px);
  font-weight: 700;
  line-height: 0.8;
  color: #a3e635;
}

.big-number-label {
  font-size: clamp(14px, 1.1vw, 18px);
  font-weight: 600;
  color: #0f172a;
  line-height: 1.2;
}

.features-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.features-list li {
  position: relative;
  padding-left: 16px;
  font-size: clamp(11.5px, 0.8vw, 13.5px);
  color: #475569;
  margin-bottom: 6px;
}

.features-list li::before {
  content: '•';
  position: absolute;
  left: 0;
  color: #0f172a;
}

/* SECTION DIVIDER */
.section-divider {
  border: 0;
  height: 1px;
  background-color: #e2e8f0;
  margin: clamp(40px, 6vh, 64px) 0;
}

/* STANDARDIZED SECTION HEADER */
.header-container {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  gap: clamp(20px, 3.5vw, 48px);
  margin-bottom: clamp(24px, 4.5vh, 56px);
}

.header-left {
  flex: 1;
}

.header-left h2 {
  margin: 0;
  font-size: clamp(22px, 2.2vw, 36px);
  font-weight: 600;
  color: #0f172a;
  line-height: 1.2;
}

.header-right {
  flex: 1;
}

.header-right p {
  margin: 0;
  font-size: clamp(12px, 0.9vw, 15px);
  line-height: 1.5;
  color: #64748b;
}

/* TIMELINE TRACK & CONTROLS */
.timeline-wrapper {
  display: flex;
  align-items: center;
  gap: clamp(10px, 1.2vw, 20px);
  margin-bottom: clamp(28px, 5vh, 64px);
}

.nav-arrow {
  width: clamp(28px, 2.5vw, 38px);
  height: clamp(28px, 2.5vw, 38px);
  border-radius: 50%;
  border: 1px solid #cbd5e1;
  background: #ffffff;
  color: #0f172a;
  font-size: clamp(13px, 1.1vw, 18px);
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  transition: all 0.2s ease;
  flex-shrink: 0;
}

.nav-arrow:hover:not(:disabled) {
  background: #a3e635;
  color: #0c0b0b;
  border-color: #03820f;
}

.nav-arrow:disabled {
  opacity: 0.4;
  cursor: not-allowed;
}

.timeline-track {
  position: relative;
  flex: 1;
  height: 2px;
  background: #cbd5e1;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.timeline-progress {
  position: absolute;
  left: 0;
  top: 0;
  height: 2px;
  background: #a3e635;
  transition: width 0.3s ease;
}

.timeline-node {
  position: relative;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  align-items: center;
  z-index: 2;
}

.node-year {
  position: absolute;
  top: clamp(-28px, -3vh, -20px);
  font-size: clamp(10px, 0.8vw, 13px);
  font-weight: 600;
  color: #64748b;
  transition: color 0.2s ease;
}

.node-dot {
  width: clamp(10px, 1vw, 16px);
  height: clamp(10px, 1vw, 16px);
  border-radius: 50%;
  background: #ffffff;
  border: 2px solid #cbd5e1;
  transition: all 0.2s ease;
}

.timeline-node.active .node-year {
  color: #0f172a;
  font-weight: 700;
}

.timeline-node.active .node-dot {
  background: #a3e635;
  border-color: #007906;
  transform: scale(1.2);
}

.timeline-node.past .node-dot {
  border-color: #007906;
}

/* CONTENT CONTAINER */
.milestone-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: clamp(20px, 3.5vw, 48px);
}

.milestone-text {
  flex: 1;
}

.active-year {
  font-size: clamp(32px, 3.5vw, 56px);
  font-weight: 500;
  color: #0f172a;
  margin: 0 0 clamp(8px, 1vh, 16px) 0;
}

.milestone-text h3 {
  font-size: clamp(15px, 1.3vw, 20px);
  font-weight: 700;
  color: #0f172a;
  margin: 0 0 clamp(8px, 1vh, 16px) 0;
}

.milestone-text p {
  font-size: clamp(12px, 0.9vw, 15px);
  line-height: 1.5;
  color: #64748b;
  margin: 0;
  max-width: clamp(300px, 32vw, 460px);
}

.milestone-image {
  flex: 1.1;
  height: clamp(240px, 35vh, 380px);
  border-radius: clamp(8px, 1.2vw, 16px);
  overflow: hidden;
}

.milestone-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

@media (max-width: 900px) {
  .champions-header,
  .champions-grid,
  .header-container, 
  .milestone-content {
    grid-template-columns: 1fr;
    flex-direction: column;
    gap: clamp(16px, 2vh, 24px);
  }

  .large-hero-card {
    height: clamp(280px, 36vh, 360px);
  }

  .milestone-image {
    width: 100%;
    height: clamp(200px, 28vh, 280px);
  }
}
</style>