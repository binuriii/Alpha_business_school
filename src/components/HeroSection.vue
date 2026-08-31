
<script setup>
import { ref } from 'vue'

const activeNav = ref('Home')

const activeTab = ref(0)

const currentSlide = ref(1)

const totalSlides = 3

const navItems = ['Home', 'Services', 'Industries', 'About']

const tabs = ref([
  {
    id: 0,
    label: 'GLOBAL QUALIFICATIONS',
    detail: 'ACCA • CFA • CPA • CIA'
  },
  {
    id: 1,
    label: 'CAREER PATHWAYS',
    detail: 'Choose the qualification that fits your ambition'
  },
  {
    id: 2,
    label: 'EXPERT-LED LEARNING',
    detail: 'Learn from industry professionals'
  }
])
</script>

<template>
  <div class="hero-wrapper">

    <!-- NAVIGATION BAR -->
    <header class="navbar">

      <!-- LOGO -->
      <div class="logo">
        <img
          src="/images/logo.png"
          alt="Alpha Business School"
          class="logo-image"
        />
      </div>

      <!-- NAVIGATION LINKS -->
      <nav class="nav-links">

        <div
          v-for="item in navItems"
          :key="item"
          class="nav-item"
          :class="{ active: activeNav === item }"
          @click="activeNav = item"
        >
          <span>{{ item }}</span>

          <svg
            class="dropdown-icon"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
          >
            <path d="M6 9l6 6 6-6" />
          </svg>
        </div>

        <a
          href="#"
          class="nav-pill"
          :class="{ active: activeNav === 'Insight' }"
          @click.prevent="activeNav = 'Insight'"
        >
          Insight
        </a>

      </nav>

      <!-- HEADER ACTIONS -->
      <div class="header-actions">

        <!-- SEARCH -->
        <button
          class="icon-btn"
          aria-label="Search"
        >
          <svg
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
          >
            <circle
              cx="11"
              cy="11"
              r="8"
            />
            <path d="M21 21l-4.35-4.35" />
          </svg>
        </button>

        <!-- CONTACT -->
        <button class="btn-primary">
          Contact Us
        </button>

      </div>
    </header>


    <!-- HERO MAIN SECTION -->
    <section class="hero-section">

      <!-- BACKGROUND IMAGE -->
      <div class="hero-bg">

        <img
          src="https://images.unsplash.com/photo-1787051503167-1a7653c0e94b?q=80&w=2429&auto=format&fit=crop"
          alt="Consulting session"
        />

        <div class="hero-overlay"></div>

      </div>


      <!-- HERO CONTENT -->
      <div class="hero-content">

        <h1 class="hero-title">
          Build the Career

          <span class="title-line"></span>

          <br />

          You’re Meant For.
        </h1>

        <button class="btn-action">

          <span>
            Explore Qualifications
          </span>

          <span class="action-icon">

            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2.5"
            >
              <path d="M7 17L17 7M17 7H7M17 7V17" />
            </svg>

          </span>

        </button>

      </div>


      <!-- VERTICAL SLIDER -->
      <div class="vertical-slider-nav">

        <span class="slider-num">
          01
        </span>

        <div class="slider-track">

          <div
            class="slider-thumb"
            :style="{
              height: `${(currentSlide / totalSlides) * 100}%`
            }"
          ></div>

        </div>

        <span class="slider-num">
          03
        </span>

      </div>


      <!-- BOTTOM TABS -->
      <div class="bottom-tabs-bar">

        <button
          v-for="(tab, index) in tabs"
          :key="tab.id"
          class="tab-item"
          :class="{
            active: activeTab === index && index === 0
          }"
          :disabled="index !== 0"
          @click="index === 0 && (activeTab = index)"
        >

          <span class="tab-label">
            {{ tab.label }}
          </span>

          <span class="tab-detail">
            {{ tab.detail }}
          </span>

        </button>

      </div>

    </section>

  </div>
</template>


<style scoped>

.hero-wrapper {
  position: relative;
  width: 100%;
  min-height: 100vh;
  background-color: #ffffff;
  box-sizing: border-box;
  padding: 16px;

  font-family:
    'Oakes Grotesk',
    'Urbanist',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    sans-serif;
}


/* =========================================
   NAVBAR
========================================= */

.navbar {
  position: fixed;

  top: 32px;
  left: 48px;
  right: 48px;

  z-index: 100;

  display: flex;
  align-items: center;
  justify-content: space-between;
}


/* =========================================
   LOGO
========================================= */

.logo {
  display: flex;
  align-items: center;
  flex-shrink: 0;
}

.logo-image {
  width: 105px;
  height: auto;
  display: block;
  object-fit: contain;
}

/* =========================================
   NAVIGATION
========================================= */

.nav-links {
  display: flex;
  align-items: center;
  gap: 8px;

  background: rgba(255, 255, 255, 0.1);

  backdrop-filter: blur(12px);

  padding: 6px 8px;

  border-radius: 40px;

  border: 1px solid rgba(255, 255, 255, 0.15);
}


.nav-item {
  display: flex;
  align-items: center;
  gap: 4px;

  color: rgba(255, 255, 255, 0.8);

  font-size: 14px;
  font-weight: 500;

  padding: 8px 16px;

  border-radius: 20px;

  cursor: pointer;

  transition:
    all 0.2s ease;
}


.nav-item:hover {
  color: #ffffff;
}


.nav-item.active {
  background: #ffffff;

  color: #0f172a;

  font-weight: 600;
}


.dropdown-icon {
  width: 14px;
  height: 14px;
}


.nav-pill {
  color: rgba(255, 255, 255, 0.8);

  padding: 8px 18px;

  border-radius: 20px;

  text-decoration: none;

  font-size: 13px;
  font-weight: 500;

  transition:
    all 0.2s ease;
}


.nav-pill:hover {
  color: #ffffff;
}


.nav-pill.active {
  background: #ffffff;

  color: #0f172a;

  font-weight: 600;
}


/* =========================================
   HEADER ACTIONS
========================================= */

.header-actions {
  display: flex;
  align-items: center;
  gap: 12px;
}


.icon-btn {
  width: 42px;
  height: 42px;

  border-radius: 50%;

  background: rgba(255, 255, 255, 0.85);

  border: none;

  display: flex;
  align-items: center;
  justify-content: center;

  cursor: pointer;

  transition:
    transform 0.2s ease;
}


.icon-btn:hover {
  transform: scale(1.05);
}


.icon-btn svg {
  width: 18px;
  height: 18px;

  stroke: #0f172a;
}


.btn-primary {
  background: #a3e635;

  color: #0f172a;

  border: none;

  padding: 12px 24px;

  border-radius: 24px;

  font-size: 14px;
  font-weight: 600;

  cursor: pointer;

  transition:
    opacity 0.2s ease;
}


.btn-primary:hover {
  opacity: 0.9;
}


/* =========================================
   HERO SECTION
========================================= */

.hero-section {
  position: relative;

  width: 100%;

  height: calc(100vh - 32px);

  border-radius: 24px;

  overflow: hidden;

  display: flex;
  align-items: center;

  padding: 0 64px;

  box-sizing: border-box;
}


/* =========================================
   HERO BACKGROUND
========================================= */

.hero-bg {
  position: absolute;

  inset: 0;

  width: 100%;
  height: 100%;

  z-index: 1;
}


.hero-bg img {
  width: 100%;
  height: 100%;

  object-fit: cover;
}


.hero-overlay {
  position: absolute;

  inset: 0;

  width: 100%;
  height: 100%;

  background:
    linear-gradient(
      90deg,
      rgba(0, 0, 0, 0.55) 0%,
      rgba(0, 0, 0, 0.15) 60%,
      rgba(0, 0, 0, 0) 100%
    );
}


/* =========================================
   HERO CONTENT
========================================= */

.hero-content {
  position: relative;

  z-index: 2;

  max-width: 600px;
}


.hero-title {
  font-size: clamp(38px, 4.5vw, 64px);

  font-weight: 500;

  color: #ffffff;

  line-height: 1.15;

  margin: 0 0 36px 0;

  letter-spacing: -1px;
}


.title-line {
  display: inline-block;

  width: 80px;
  height: 2px;

  background-color: #a3e635;

  vertical-align: middle;

  margin-left: 8px;
}


/* =========================================
   HERO BUTTON
========================================= */

.btn-action {
  display: inline-flex;

  align-items: center;

  gap: 12px;

  background: #a3e635;

  color: #0f172a;

  border: none;

  padding: 6px 6px 6px 24px;

  border-radius: 30px;

  font-size: 15px;

  font-weight: 600;

  cursor: pointer;

  transition:
    transform 0.2s ease;
}


.btn-action:hover {
  transform: translateY(-2px);
}


.action-icon {
  width: 36px;
  height: 36px;

  border-radius: 50%;

  background: rgba(0, 0, 0, 0.1);

  display: flex;

  align-items: center;

  justify-content: center;
}


.action-icon svg {
  width: 16px;
  height: 16px;

  stroke: #0f172a;
}


/* =========================================
   VERTICAL SLIDER
========================================= */

.vertical-slider-nav {
  position: absolute;

  right: 48px;

  top: 50%;

  transform: translateY(-50%);

  z-index: 2;

  display: flex;

  flex-direction: column;

  align-items: center;

  gap: 12px;

  color: rgba(255, 255, 255, 0.6);

  font-size: 12px;
}


.slider-track {
  width: 2px;

  height: 100px;

  background: rgba(255, 255, 255, 0.2);

  position: relative;

  border-radius: 2px;
}


.slider-thumb {
  width: 100%;

  background: #a3e635;

  position: absolute;

  top: 0;
  left: 0;

  border-radius: 2px;

  transition:
    height 0.3s ease;
}


/* =========================================
   BOTTOM TABS
========================================= */

.bottom-tabs-bar {
  position: absolute;

  bottom: 32px;

  left: 64px;
  right: 64px;

  z-index: 2;

  display: flex;

  gap: 16px;
}


.tab-item {
  flex: 1;

  display: flex;

  flex-direction: column;

  justify-content: center;

  gap: 5px;

  background: rgba(255, 255, 255, 0.2);

  backdrop-filter: blur(16px);

  border: 1px solid rgba(255, 255, 255, 0.2);

  border-radius: 16px;

  padding: 10px 25px;

  min-height: 72px;

  color: rgba(255, 255, 255, 0.7);

  text-align: left;

  cursor: default;

  transition:
    background 0.3s ease,
    color 0.3s ease,
    border-color 0.3s ease,
    transform 0.3s ease;
}


.tab-item:hover {
  background: rgba(255, 255, 255, 0.3);

  color: #ffffff;

  transform: translateY(-2px);
}


.tab-item:disabled {
  opacity: 1;
}


.tab-label {
  display: block;

  font-size: 12px;

  font-weight: 700;

  letter-spacing: 0.8px;

  line-height: 1.2;
}


.tab-detail {
  display: block;

  font-size: 12px;

  font-weight: 400;

  letter-spacing: 0;

  line-height: 1.4;

  opacity: 0.8;
}


.tab-item.active .tab-detail {
  opacity: 0.65;
}


/* =========================================
   TABLET
========================================= */

@media (max-width: 1100px) {

  .navbar {
    left: 32px;
    right: 32px;
  }


  .logo-image {
    width: 135px;
  }


  .hero-section {
    padding: 0 40px;
  }


  .bottom-tabs-bar {
    left: 40px;
    right: 40px;
  }

}


/* =========================================
   SMALL TABLET
========================================= */

@media (max-width: 900px) {

  .navbar {
    left: 24px;
    right: 24px;
  }


  .nav-links {
    display: none;
  }


  .hero-section {
    padding: 0 24px;
  }


  .hero-title {
    font-size: clamp(36px, 7vw, 52px);
  }


  .bottom-tabs-bar {
    left: 24px;
    right: 24px;

    flex-direction: column;

    gap: 8px;
  }


  .tab-item {
    min-height: auto;

    padding: 10px;
  }

}


/* =========================================
   MOBILE
========================================= */

@media (max-width: 600px) {

  .hero-wrapper {
    padding: 8px;
  }


  .hero-section {
    height: calc(100vh - 16px);

    border-radius: 18px;

    padding: 0 20px;
  }


  .navbar {
    top: 22px;

    left: 20px;
    right: 20px;
  }


  .logo-image {
    width: 115px;
  }


  .btn-primary {
    padding: 10px 16px;

    font-size: 12px;
  }


  .icon-btn {
    width: 38px;
    height: 38px;
  }


  .hero-content {
    max-width: 90%;
  }


  .hero-title {
    font-size: clamp(34px, 10vw, 46px);

    margin-bottom: 28px;
  }


  .title-line {
    width: 50px;
  }


  .vertical-slider-nav {
    right: 20px;
  }


  .bottom-tabs-bar {
    bottom: 20px;

    left: 20px;
    right: 20px;
  }


  .tab-item {
    padding: 10px;

    border-radius: 12px;
  }


  .tab-label {
    font-size: 10px;
  }


  .tab-detail {
    font-size: 10px;
  }

}

</style>

