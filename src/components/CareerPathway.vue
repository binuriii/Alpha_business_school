<script setup>
import { ref } from 'vue'

const scrollContainer = ref(null)
const activeIndex = ref(0)

const pathways = ref([
  {
    id: 1,
    title: 'Financial Modeler & Corporate Finance Specialist',
    qualifications: 'AFM (FMI Canada)',
    image: 'https://images.unsplash.com/photo-1758518730037-a16581a040e8?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTR8fEZpbmFuY2lhbCUyME1vZGVsZXIlMjAlMjYlMjBDb3Jwb3JhdGUlMjBGaW5hbmNlJTIwU3BlY2lhbGlzdHxlbnwwfHwwfHx8MA%3D%3D',
    badge: 'PRACTICAL SKILL',
    entryLevel: 'Students & Pros',
    duration: '3 - 6 Months',
    scope: 'Corporate & M&A',
    earningPotential: 'Skill Premium'
  },
  {
    id: 2,
    title: 'Chief Risk Officer & Financial Risk Manager',
    qualifications: 'FRM® (GARP USA)',
    image: 'https://images.unsplash.com/photo-1622675363311-3e1904dc1885?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDF8fHxlbnwwfHx8fHw%3D',
    badge: 'BANKING BENCHMARK',
    entryLevel: 'Undergrads & Pros',
    duration: '1 - 2 Years',
    scope: 'Risk & Governance',
    earningPotential: 'Top Tier'
  },
  {
    id: 3,
    title: 'Senior Internal Auditor & Compliance Head',
    qualifications: 'CIA® (IIA USA)',
    image: 'https://images.unsplash.com/photo-1657727534676-cac1bb160d64?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Mnx8U2VuaW9yJTIwSW50ZXJuYWwlMjBBdWRpdG9yJTIwJTI2JTIwQ29tcGxpYW5jZSUyMEhlYWR8ZW58MHx8MHx8fDA%3D',
    badge: 'GLOBALLY CERTIFIED',
    entryLevel: 'Audit Professionals',
    duration: '1 - 1.5 Years',
    scope: 'Audit & Assurance',
    earningPotential: 'High Growth'
  },
  {
    id: 4,
    title: 'Australian CPA & Migration Pathway Specialist',
    qualifications: 'CPA Australia',
    image: 'https://images.unsplash.com/photo-1622675205169-901710ac8643?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDd8fHxlbnwwfHx8fHw%3D',
    badge: 'PR TARGET',
    badgeType: 'highlight',
    entryLevel: 'Degree / ACCA / CA',
    duration: '1.5 - 2.5 Years',
    scope: 'Australia & APAC',
    earningPotential: 'AUD Standard'
  },
  {
    id: 5,
    title: 'Investment Banker & Portfolio Manager',
    qualifications: 'CFA® • CAIA',
    image: 'https://images.unsplash.com/photo-1714974528683-8940bd8311aa?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTZ8fENoaWVmJTIwUmlzayUyME9mZmljZXIlMjAlMjYlMjBGaW5hbmNpYWwlMjBSaXNrJTIwTWFuYWdlcnxlbnwwfHwwfHx8MA%3D%3D',
    badge: 'HIGH DEMAND',
    badgeType: 'highlight',
    entryLevel: 'After A/L or Degree',
    duration: '2 - 3 Years',
    scope: 'Global Markets',
    earningPotential: 'Top Tier'
  },
  {
    id: 6,
    title: 'Chartered Certified Accountant & CFO',
    qualifications: 'ACCA UK • B.Sc. (Hons)',
    image: 'https://images.unsplash.com/photo-1577962917302-cd874c4e31d2?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8ODB8fENoYXJ0ZXJlZCUyMENlcnRpZmllZCUyMEFjY291bnRhbnQlMjAlMjYlMjBDRk98ZW58MHx8MHx8fDA%3D',
    badge: 'GLOBAL MOBILITY',
    badgeType: 'highlight',
    entryLevel: 'After O/L or A/L',
    duration: '2 - 3 Years',
    scope: '180+ Countries',
    earningPotential: 'High Growth'
  },
  {
    id: 7,
    title: 'Management Accountant & Business Analyst',
    qualifications: 'CIMA UK',
    image: 'https://plus.unsplash.com/premium_photo-1736640213486-8ba82c6dc466?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDR8fHxlbnwwfHx8fHw%3D',
    badge: 'STRATEGIC FINANCE',
    entryLevel: 'Students & Graduates',
    duration: '2 - 3 Years',
    scope: 'Corporate Strategy',
    earningPotential: 'High Growth'
  },
  {
    id: 8,
    title: 'Tax Consultant & Forensic Auditor',
    qualifications: 'Chartered Tax Professional',
    image: 'https://images.unsplash.com/photo-1622675103136-e4b90c9a33d6?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDd8fHxlbnwwfHx8fHw%3D',
    badge: 'SPECIALIST',
    entryLevel: 'Accountants & Law',
    duration: '1 Year',
    scope: 'Tax & Compliance',
    earningPotential: 'Premium'
  }
])

const scrollToCard = (index) => {
  if (!scrollContainer.value) return
  
  if (index < 0) {
    index = pathways.value.length - 1
  } else if (index >= pathways.value.length) {
    index = 0
  }
  
  const cards = scrollContainer.value.querySelectorAll('.pathway-card')
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
  <section class="pathways-section">
    <!-- SECTION HEADER -->
    <div class="section-header">
      <h2 class="section-title">Explore Career Pathways</h2>
      <p class="section-subtitle">Discover global qualifications aligned with high-paying finance, accounting, and audit roles.</p>
    </div>

    <div class="carousel-relative-container">
      <!-- SIDE SCROLL BUTTONS -->
      <button class="nav-arrow prev-arrow" @click="prevSlide" aria-label="Previous pathway">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
          <path d="M15 18l-6-6 6-6"/>
        </svg>
      </button>

      <!-- CAROUSEL TRACK -->
      <div class="pathways-track" ref="scrollContainer">
        <div 
          v-for="(pathway, index) in pathways" 
          :key="pathway.id"
          :id="`pathway-card-${pathway.id}`"
          class="pathway-card"
          :class="{ 'card-active': index === activeIndex }"
          @click="scrollToCard(index)"
        >
          <!-- MEDIA -->
          <div class="card-media">
            <img :src="pathway.image" :alt="pathway.title" />
            <span 
              class="badge"
              :class="{ 'badge-green': pathway.badgeType === 'highlight' }"
            >
              {{ pathway.badge }}
            </span>
          </div>

          <!-- CARD CONTENT -->
          <div class="card-content">
            <h3 class="pathway-title">{{ pathway.title }}</h3>
            <p class="qualifications-text">{{ pathway.qualifications }}</p>

            <!-- 2x2 META GRID -->
            <div class="meta-grid">
              <div class="meta-item">
                <span class="meta-label">ENTRY LEVEL</span>
                <span class="meta-value">{{ pathway.entryLevel }}</span>
              </div>
              <div class="meta-item">
                <span class="meta-label">DURATION</span>
                <span class="meta-value">{{ pathway.duration }}</span>
              </div>
              <div class="meta-item">
                <span class="meta-label">SCOPE</span>
                <span class="meta-value">{{ pathway.scope }}</span>
              </div>
              <div class="meta-item">
                <span class="meta-label">EARNING POTENTIAL</span>
                <span class="meta-value">{{ pathway.earningPotential }}</span>
              </div>
            </div>

            <!-- BUTTON WITH RIGHT ARROW -->
            <button class="explore-btn" @click.stop="scrollToCard(index)">
              <span>View Pathway</span>
              <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
                <path d="M5 12h14M12 5l7 7-7 7"/>
              </svg>
            </button>
          </div>
        </div>
      </div>

      <button class="nav-arrow next-arrow" @click="nextSlide" aria-label="Next pathway">
        <svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.5">
          <path d="M9 18l6-6-6-6"/>
        </svg>
      </button>
    </div>
  </section>
</template>

<style scoped>
/* MAIN CONTAINER WITH FLUID VIEWPORT UNITS & CLAMP */
.pathways-section {
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

.section-header {
  margin-bottom: clamp(16px, 3vh, 32px);
}

.section-title {
  margin: 0 0 clamp(4px, 1vh, 10px) 0;
  font-size: clamp(22px, 2.2vw, 36px);
  font-weight: 600;
  color: #0f172a;
  line-height: 1.2;
  font-family: inherit;
}

.section-subtitle {
  margin: 0;
  font-size: clamp(12px, 0.9vw, 15px);
  line-height: 1.5;
  color: #64748b;
  font-family: inherit;
}

.carousel-relative-container {
  position: relative;
  width: 100%;
}

.pathways-track {
  display: flex;
  gap: clamp(12px, 1.5vw, 24px);
  overflow-x: auto;
  scroll-behavior: smooth;
  scrollbar-width: none;
  padding: clamp(3px, 0.4vh, 6px) 0 clamp(8px, 1.2vh, 16px) 0;
}

.pathways-track::-webkit-scrollbar {
  display: none;
}

.pathway-card {
  flex: 0 0 calc(25% - clamp(9px, 1.1vw, 18px));
  min-width: clamp(230px, 20vw, 280px);
  background: #ffffff;
  border: 1px solid #e2e8f0;
  border-radius: clamp(10px, 1.2vw, 18px);
  overflow: hidden;
  display: flex;
  flex-direction: column;
  cursor: pointer;
  transition: transform 0.3s ease, box-shadow 0.3s ease, border-color 0.3s ease;
}

.pathway-card:hover, .pathway-card.card-active {
  transform: translateY(-0.5vh);
  box-shadow: 0 10px 20px rgba(15, 23, 42, 0.08);
}

.card-media {
  position: relative;
  width: 100%;
  height: clamp(120px, 18vh, 180px);
  overflow: hidden;
  background-color: #0f172a;
}

.card-media img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}

.badge {
  position: absolute;
  top: clamp(8px, 1.2vh, 14px);
  left: clamp(8px, 1vw, 14px);
  background: #f1f2f5;
  color: #0f0f0f;
  font-size: clamp(9px, 0.65vw, 11px);
  font-weight: 700;
  padding: clamp(3px, 0.4vh, 6px) clamp(6px, 0.6vw, 10px);
  border-radius: clamp(3px, 0.3vw, 6px);
  letter-spacing: 0.5px;
  font-family: inherit;
}

.badge-green {
  background: #a3e635;
  color: #000000;
}

.card-content {
  padding: clamp(14px, 2vh, 24px) clamp(12px, 1.2vw, 20px);
  display: flex;
  flex-direction: column;
  flex: 1;
}

.pathway-title {
  font-size: clamp(13px, 1vw, 16px);
  font-weight: 600;
  color: #0f172a;
  margin: 0 0 clamp(4px, 0.6vh, 8px) 0;
  line-height: 1.35;
  font-family: inherit;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
  height: clamp(34px, 4.5vh, 44px);
}

.qualifications-text {
  font-size: clamp(10.5px, 0.8vw, 13px);
  font-weight: 700;
  color: #007906;
  margin: 0 0 clamp(10px, 1.6vh, 20px) 0;
  font-family: inherit;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.meta-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: clamp(8px, 1vh, 14px) clamp(6px, 0.6vw, 10px);
  margin-bottom: clamp(14px, 2vh, 24px);
  background: #f8fafc;
  padding: clamp(10px, 1.4vh, 16px);
  border-radius: clamp(6px, 0.8vw, 12px);
}

.meta-item {
  display: flex;
  flex-direction: column;
  gap: 2px;
}

.meta-label {
  font-size: clamp(8px, 0.6vw, 10px);
  color: #94a3b8;
  font-weight: 700;
  letter-spacing: 0.3px;
  font-family: inherit;
}

.meta-value {
  font-size: clamp(10px, 0.75vw, 12px);
  font-weight: 600;
  color: #0f172a;
  font-family: inherit;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.explore-btn {
  margin-top: auto;
  width: 100%;
  padding: clamp(8px, 1vh, 12px) clamp(10px, 1vw, 16px);
  background-color: #000000;
  border: 1px solid #cbd5e1;
  border-radius: clamp(6px, 0.6vw, 10px);
  color: #ffffff;
  font-size: clamp(11.5px, 0.85vw, 14px);
  font-weight: 700;
  font-family: inherit;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: clamp(4px, 0.4vw, 8px);
  cursor: pointer;
  transition: all 0.2s ease;
}

.explore-btn svg {
  width: clamp(12px, 0.9vw, 16px);
  height: clamp(12px, 0.9vw, 16px);
  stroke: #ffffff;
  
}

.explore-btn:hover {
  background-color: #1f1e1e;
  color: #ffffff;
}

.nav-arrow {
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

.nav-arrow:hover {
  border-color: #0f172a;
  background-color: #f1f5f9;
}

.nav-arrow svg {
  width: clamp(12px, 1vw, 18px);
  height: clamp(12px, 1vw, 18px);
  stroke: #0f172a;
}

.prev-arrow {
  left: clamp(-20px, -1.2vw, -12px);
}

.next-arrow {
  right: clamp(-20px, -1.2vw, -12px);
}

/* RESPONSIVE BREAKPOINTS */
@media (max-width: 1024px) {
  .pathway-card {
    flex: 0 0 calc(33.333% - clamp(8px, 1vw, 16px));
  }
}

@media (max-width: 768px) {
  .pathway-card {
    flex: 0 0 calc(50% - clamp(6px, 0.8vw, 12px));
  }
  .nav-arrow {
    display: none;
  }
}

@media (max-width: 480px) {
  .pathway-card {
    flex: 0 0 85vw;
  }
}
</style>