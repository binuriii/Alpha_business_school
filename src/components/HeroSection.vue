<script setup>
import {
  ref,
  onMounted,
  onUnmounted
} from 'vue'


/* =========================================
   NAVIGATION STATE
========================================= */

const activeNav = ref('Home')
const activeTab = ref(0)


/* =========================================
   DROPDOWN STATE
========================================= */

const openDropdown = ref(null)
const navLinksRef = ref(null)

const toggleDropdown = (label) => {
  openDropdown.value =
    openDropdown.value === label
      ? null
      : label
}

const closeDropdowns = () => {
  openDropdown.value = null
}

const handleOutsideClick = (event) => {
  if (
    navLinksRef.value &&
    !navLinksRef.value.contains(event.target)
  ) {
    closeDropdowns()
  }
}


/* =========================================
   HERO SLIDESHOW
========================================= */

const currentSlide = ref(0)

const slides = [
  {
    id: 1,
    image:
      'images/hero1.png',
    alt: 'Alpha Business School'
  },

  {
    id: 2,
    image:
      'images/hero2.png',
    alt: 'CFA students'
  },

  {
    id: 3,
    image:
      'images/hero3.png',
    alt: 'Alpha Business School campus'
  }
]

const totalSlides = slides.length

let slideInterval = null


/* NEXT SLIDE */

const nextSlide = () => {
  currentSlide.value =
    (currentSlide.value + 1) %
    totalSlides
}


/* PREVIOUS SLIDE */

const previousSlide = () => {
  currentSlide.value =
    (
      currentSlide.value -
      1 +
      totalSlides
    ) %
    totalSlides
}


/* GO TO SPECIFIC SLIDE */

const goToSlide = (index) => {
  currentSlide.value = index

  restartSlider()
}


/* START AUTO SLIDESHOW */

const startSlider = () => {
  stopSlider()

  slideInterval = setInterval(() => {
    nextSlide()
  }, 3000)
}


/* STOP SLIDESHOW */

const stopSlider = () => {
  if (slideInterval) {
    clearInterval(slideInterval)

    slideInterval = null
  }
}


/* RESTART AFTER MANUAL CLICK */

const restartSlider = () => {
  stopSlider()
  startSlider()
}


/* =========================================
   HEADER SCROLL STATE
========================================= */

const isScrolled = ref(false)

const handleScroll = () => {
  isScrolled.value =
    window.scrollY > 40
}


/* =========================================
   LOGO FALLBACK
========================================= */

const darkLogoFailed = ref(false)

const handleDarkLogoError = () => {
  darkLogoFailed.value = true
}


/* =========================================
   NAV ITEMS — Alpha Business School / CFA
========================================= */

const navItems = [
  {
    label: 'Home',
    submenu: null
  },
  {
    label: 'ACCA',
    submenu: [
      'ACCA Fundamentals',
      'ACCA Professional',
      'ACCA Fees',
      'ACCA Lecture Panel'
    ]
  },
  {
    label: 'CFA',
    submenu: [
      'CFA Level I',
      'CFA Fees',
      'CFA Lecture Panel',
      'CFA Application'
    ]
  },
  {
    label: 'CPA Australia',
    submenu: [
      'CPA Program',
      'CPA Fees',
      'CPA Lecture Panel'
    ]
  },
  {
    label: 'About Us',
    submenu: [
      'Our Story',
      'Management Team',
      'Contact Us'
    ]
  }
]


/* =========================================
   REAL CONTACT NUMBER
========================================= */

const phoneNumber = '+94 77 365 4254'
const phoneHref = 'tel:+94773654254'


/* =========================================
   HERO BOTTOM TABS — CFA program highlights
========================================= */

const tabs = ref([
  {
    id: 0,
    label: 'GLOBAL CREDENTIAL',
    detail: 'Chartered Financial Analyst® (CFA), CFA Institute'
  },

  {
    id: 1,
    label: 'VETERAN CFA PANEL',
    detail:
      "Sri Lanka's only CFA Charterholder lecture panel"
  },

  {
    id: 2,
    label: 'NOV / MAY INTAKES',
    detail:
      '250+ hours of live lectures & recorded access'
  }
])


/* =========================================
   COMPONENT MOUNTED
========================================= */

onMounted(() => {

  window.addEventListener(
    'scroll',
    handleScroll,
    {
      passive: true
    }
  )

  document.addEventListener(
    'click',
    handleOutsideClick
  )

  /* LOAD FONT AWESOME IF NOT ALREADY PRESENT */

  if (
    !document.getElementById(
      'fa-icons-cdn'
    )
  ) {
    const faLink =
      document.createElement('link')

    faLink.id = 'fa-icons-cdn'
    faLink.rel = 'stylesheet'
    faLink.href =
      'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css'

    document.head.appendChild(faLink)
  }

  handleScroll()

  startSlider()
})


/* =========================================
   COMPONENT DESTROY
========================================= */

onUnmounted(() => {

  window.removeEventListener(
    'scroll',
    handleScroll
  )

  document.removeEventListener(
    'click',
    handleOutsideClick
  )

  stopSlider()
})
</script>


<template>

  <div class="hero-wrapper">


    <!-- =========================================
         NAVIGATION BAR
    ========================================== -->

    <header
      class="navbar"
      :class="{
        scrolled: isScrolled
      }"
    >


      <!-- =========================================
           LOGO
      ========================================== -->

      <div class="logo">


        <!-- NORMAL HERO LOGO -->

        <img
          v-if="!isScrolled"
          src="/images/logo.png"
          alt="Alpha Business School"
          class="logo-image"
        />


        <!-- SCROLLED HEADER LOGO -->

        <img
          v-else-if="!darkLogoFailed"
          src="/images/logo-dark.png"
          alt="Alpha Business School"
          class="logo-image"
          @error="handleDarkLogoError"
        />


        <!-- FALLBACK IF DARK LOGO DOESN'T EXIST -->

        <img
          v-else
          src="/images/logo.png"
          alt="Alpha Business School"
          class="logo-image logo-fallback-dark"
        />

      </div>


      <!-- =========================================
           NAVIGATION LINKS
      ========================================== -->

      <nav
        class="nav-links"
        ref="navLinksRef"
      >

        <div
          v-for="item in navItems"
          :key="item.label"
          class="nav-item-wrapper"
        >

          <div
            class="nav-item"
            :class="{
              active:
                activeNav === item.label,
              'has-open-dropdown':
                openDropdown === item.label
            }"
            @click="
              activeNav = item.label;
              item.submenu
                ? toggleDropdown(item.label)
                : closeDropdowns()
            "
          >

            <span>
              {{ item.label }}
            </span>


            <i
              v-if="item.submenu"
              class="fa-solid fa-chevron-down dropdown-icon"
              :class="{
                open:
                  openDropdown === item.label
              }"
            ></i>

          </div>


          <!-- SUBMENU -->

          <transition name="dropdown-fade">

            <div
              v-if="
                item.submenu &&
                openDropdown === item.label
              "
              class="dropdown-menu"
            >

              <a
                v-for="sub in item.submenu"
                :key="sub"
                href="#"
                class="dropdown-menu-item"
                @click.prevent="
                  closeDropdowns()
                "
              >
                {{ sub }}
              </a>

            </div>

          </transition>

        </div>


        <!-- APPLY NOW -->

        <a
          href="#"
          class="nav-pill"
          :class="{
            active:
              activeNav === 'Apply Now'
          }"
          @click.prevent="
            activeNav = 'Apply Now';
            closeDropdowns()
          "
        >
          Apply Now
        </a>

      </nav>


      <!-- =========================================
           HEADER ACTIONS
      ========================================== -->

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

            <path
              d="M21 21l-4.35-4.35"
            />

          </svg>

        </button>


        <!-- CONTACT (real number) -->

        <a
          :href="phoneHref"
          class="btn-primary"
          :title="phoneNumber"
        >
          Contact Us
        </a>

      </div>

    </header>


    <!-- =========================================
         HERO MAIN SECTION
    ========================================== -->

    <section
      class="hero-section"
      @mouseenter="stopSlider"
      @mouseleave="startSlider"
    >


      <!-- =========================================
           HERO IMAGE SLIDESHOW
      ========================================== -->

      <div class="hero-bg">


        <img
          v-for="(slide, index) in slides"
          :key="slide.id"
          :src="slide.image"
          :alt="slide.alt"
          class="hero-slide"
          :class="{
            active:
              currentSlide === index
          }"
        />


        <!-- DARK GRADIENT -->

        <div class="hero-overlay"></div>

      </div>


      <!-- =========================================
           HERO CONTENT
      ========================================== -->

      <div class="hero-content">

        <h1 class="hero-title">

          Built the Career

          <span class="title-line"></span>

          <br />

          You're meant for

        </h1>


        <button class="btn-action">

          <span>
            Explore the CFA Program
          </span>


          <span class="action-icon">

            <svg
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2.5"
            >

              <path
                d="
                  M7 17L17 7
                  M17 7H7
                  M17 7V17
                "
              />

            </svg>

          </span>

        </button>

      </div>


      <!-- =========================================
           VERTICAL SLIDER INDICATOR
      ========================================== -->

      <div class="vertical-slider-nav">


        <!-- CURRENT SLIDE -->

        <button
          class="slider-number-button"
          type="button"
          aria-label="Previous slide"
          @click="
            previousSlide();
            restartSlider()
          "
        >

          {{
            String(
              currentSlide + 1
            ).padStart(
              2,
              '0'
            )
          }}

        </button>


        <!-- SLIDER TRACK -->

        <div
          class="slider-track"
          @click="
            nextSlide();
            restartSlider()
          "
        >

          <div
            class="slider-thumb"
            :style="{
              height:
                `${
                  (
                    (
                      currentSlide +
                      1
                    ) /
                    totalSlides
                  ) *
                  100
                }%`
            }"
          ></div>

        </div>


        <!-- TOTAL SLIDES -->

        <button
          class="slider-number-button"
          type="button"
          aria-label="Next slide"
          @click="
            nextSlide();
            restartSlider()
          "
        >

          {{
            String(
              totalSlides
            ).padStart(
              2,
              '0'
            )
          }}

        </button>

      </div>


      <!-- =========================================
           SLIDE DOTS
      ========================================== -->

      <div class="hero-dots">

        <button
          v-for="(slide, index) in slides"
          :key="`dot-${slide.id}`"
          type="button"
          class="hero-dot"
          :class="{
            active:
              currentSlide === index
          }"
          :aria-label="
            `Go to slide ${
              index + 1
            }`
          "
          @click="
            goToSlide(index)
          "
        ></button>

      </div>


      <!-- =========================================
           BOTTOM TABS
      ========================================== -->

      <div class="bottom-tabs-bar">

        <button
          v-for="(tab, index) in tabs"
          :key="tab.id"
          class="tab-item"
          :class="{
            active:
              activeTab === index &&
              index === 0
          }"
          :disabled="
            index !== 0
          "
          @click="
            index === 0 &&
            (
              activeTab =
                index
            )
          "
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

/* =========================================
   HERO WRAPPER
========================================= */

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

  overflow: hidden;
}


/* =========================================
   NAVBAR
========================================= */

.navbar {

  position: absolute;

  top: 32px;

  left: 48px;
  right: 48px;

  z-index: 1000;

  display: flex;

  align-items: center;

  justify-content:
    space-between;

  box-sizing:
    border-box;

  transition:
    top 0.3s ease,
    left 0.3s ease,
    right 0.3s ease,
    padding 0.3s ease,
    background 0.3s ease,
    box-shadow 0.3s ease;
}


/* =========================================
   SCROLLED HEADER
========================================= */

.navbar.scrolled {

  position: fixed;

  top: 0;

  left: 0;
  right: 0;

  padding:
    10px
    48px;

  background:
    #ffffff;

  box-shadow:
    0
    8px
    28px
    rgba(
      15,
      23,
      42,
      0.12
    );

  z-index: 1500;
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

  transition:
    opacity 0.3s ease,
    transform 0.3s ease,
    filter 0.3s ease;
}


/* FALLBACK DARK LOGO */

.logo-fallback-dark {

  filter:
    brightness(0);
}


/* =========================================
   NAVIGATION
========================================= */

.nav-links {

  display: flex;

  align-items: center;

  gap: 8px;

  background:
    rgba(
      255,
      255,
      255,
      0.1
    );

  backdrop-filter:
    blur(12px);

  -webkit-backdrop-filter:
    blur(12px);

  padding:
    6px
    8px;

  border-radius:
    40px;

  border:
    1px
    solid
    rgba(
      255,
      255,
      255,
      0.15
    );

  transition:
    background 0.3s ease,
    border-color 0.3s ease;
}


/* =========================================
   SCROLLED NAVIGATION
========================================= */

.navbar.scrolled .nav-links {

  background:
    #f4f4f5;

  border-color:
    #e4e4e7;
}


.navbar.scrolled .nav-item,
.navbar.scrolled .nav-pill {

  color:
    #475569;
}


.navbar.scrolled .nav-item:hover,
.navbar.scrolled .nav-pill:hover {

  color:
    #0f172a;

  background:
    rgba(
      15,
      23,
      42,
      0.05
    );
}


.navbar.scrolled .nav-item.active,
.navbar.scrolled .nav-pill.active {

  background:
    #ffffff;

  color:
    #0f172a;
}


/* =========================================
   NAV ITEM
========================================= */

.nav-item {

  display: flex;

  align-items: center;

  gap: 4px;

  color:
    rgba(
      255,
      255,
      255,
      0.8
    );

  font-size:
    14px;

  font-weight:
    500;

  padding:
    8px
    16px;

  border-radius:
    20px;

  cursor:
    pointer;

  transition:
    background 0.2s ease,
    color 0.2s ease;
}


.nav-item:hover {

  color:
    #ffffff;
}


.nav-item.active {

  background:
    #ffffff;

  color:
    #0f172a;

  font-weight:
    600;
}


/* =========================================
   NAV ITEM WRAPPER (for dropdown positioning)
========================================= */

.nav-item-wrapper {

  position:
    relative;
}


/* =========================================
   DROPDOWN ICON (Font Awesome)
========================================= */

.dropdown-icon {

  font-size:
    11px;

  line-height:
    1;

  transition:
    transform 0.25s ease;
}


.dropdown-icon.open {

  transform:
    rotate(180deg);
}


/* =========================================
   DROPDOWN MENU
========================================= */

.dropdown-menu {

  position:
    absolute;

  top:
    calc(100% + 10px);

  left:
    0;

  min-width:
    200px;

  background:
    #ffffff;

  border-radius:
    14px;

  box-shadow:
    0
    14px
    32px
    rgba(
      15,
      23,
      42,
      0.18
    );

  padding:
    8px;

  display:
    flex;

  flex-direction:
    column;

  gap:
    2px;

  z-index:
    2000;
}


.dropdown-menu-item {

  color:
    #475569;

  font-size:
    13px;

  font-weight:
    500;

  text-decoration:
    none;

  padding:
    9px
    14px;

  border-radius:
    9px;

  transition:
    background 0.15s ease,
    color 0.15s ease;
}


.dropdown-menu-item:hover {

  background:
    #f4f4f5;

  color:
    #0f172a;
}


/* DROPDOWN TRANSITION */

.dropdown-fade-enter-active,
.dropdown-fade-leave-active {

  transition:
    opacity 0.18s ease,
    transform 0.18s ease;
}


.dropdown-fade-enter-from,
.dropdown-fade-leave-to {

  opacity:
    0;

  transform:
    translateY(-6px);
}


/* =========================================
   APPLY NOW PILL
========================================= */

.nav-pill {

  color:
    rgba(
      255,
      255,
      255,
      0.8
    );

  padding:
    8px
    18px;

  border-radius:
    20px;

  text-decoration:
    none;

  font-size:
    13px;

  font-weight:
    500;

  transition:
    background 0.2s ease,
    color 0.2s ease;
}


.nav-pill:hover {

  color:
    #ffffff;
}


.nav-pill.active {

  background:
    #ffffff;

  color:
    #0f172a;

  font-weight:
    600;
}


/* =========================================
   HEADER ACTIONS
========================================= */

.header-actions {

  display: flex;

  align-items: center;

  gap: 12px;
}


/* =========================================
   SEARCH BUTTON
========================================= */

.icon-btn {

  width: 42px;

  height: 42px;

  border-radius:
    50%;

  background:
    rgba(
      255,
      255,
      255,
      0.85
    );

  border:
    none;

  display: flex;

  align-items:
    center;

  justify-content:
    center;

  cursor:
    pointer;

  transition:
    transform 0.2s ease,
    background 0.3s ease;
}


.navbar.scrolled .icon-btn {

  background:
    #f4f4f5;
}


.icon-btn:hover {

  transform:
    scale(1.05);
}


.icon-btn svg {

  width: 18px;

  height: 18px;

  stroke:
    #0f172a;
}


/* =========================================
   CONTACT BUTTON
========================================= */

.btn-primary {

  background:
    #a3e635;

  color:
    #0f172a;

  border:
    none;

  padding:
    12px
    24px;

  border-radius:
    24px;

  font-size:
    14px;

  font-weight:
    600;

  cursor:
    pointer;

  text-decoration:
    none;

  display:
    inline-block;

  transition:
    opacity 0.2s ease,
    transform 0.2s ease;
}


.btn-primary:hover {

  opacity: 0.9;

  transform:
    translateY(-1px);
}


/* =========================================
   HERO SECTION
========================================= */

.hero-section {

  position: relative;

  width: 100%;

  height:
    calc(
      100vh - 32px
    );

  border-radius:
    24px;

  overflow:
    hidden;

  display:
    flex;

  align-items:
    center;

  padding:
    0
    64px;

  box-sizing:
    border-box;
}


/* =========================================
   HERO BACKGROUND
========================================= */

.hero-bg {

  position:
    absolute;

  inset:
    0;

  width:
    100%;

  height:
    100%;

  z-index:
    1;

  overflow:
    hidden;

  background:
    #111827;
}


/* =========================================
   HERO SLIDES
========================================= */

.hero-slide {

  position:
    absolute;

  top:
    0;

  left:
    0;

  width:
    100%;

  height:
    100%;

  object-fit:
    cover;

  object-position:
    center;

  opacity:
    0;

  transform:
    scale(1.05);

  z-index:
    1;

  pointer-events:
    none;

  transition:
    opacity 0.7s ease,
    transform 4s ease;

}


/* ACTIVE SLIDE */

.hero-slide.active {

  opacity:
    1;

  transform:
    scale(1);

  z-index:
    2;
}


/* =========================================
   HERO OVERLAY
========================================= */

.hero-overlay {

  position:
    absolute;

  inset:
    0;

  width:
    100%;

  height:
    100%;

  z-index:
    3;

  pointer-events:
    none;

  background:
    linear-gradient(
      90deg,
      rgba(
        0,
        0,
        0,
        0.58
      )
      0%,

      rgba(
        0,
        0,
        0,
        0.25
      )
      45%,

      rgba(
        0,
        0,
        0,
        0.08
      )
      70%,

      rgba(
        0,
        0,
        0,
        0
      )
      100%
    );
}


/* =========================================
   HERO CONTENT
========================================= */

.hero-content {

  position:
    relative;

  z-index:
    5;

  max-width:
    600px;
}


/* =========================================
   HERO TITLE
========================================= */

.hero-title {

  font-size:
    clamp(
      38px,
      4.5vw,
      64px
    );

  font-weight:
    500;

  color:
    #ffffff;

  line-height:
    1.15;

  margin:
    0
    0
    36px
    0;

  letter-spacing:
    -1px;
}


/* =========================================
   GREEN LINE
========================================= */

.title-line {

  display:
    inline-block;

  width:
    80px;

  height:
    2px;

  background-color:
    #a3e635;

  vertical-align:
    middle;

  margin-left:
    8px;
}


/* =========================================
   HERO BUTTON
========================================= */

.btn-action {

  display:
    inline-flex;

  align-items:
    center;

  gap:
    12px;

  background:
    #a3e635;

  color:
    #0f172a;

  border:
    none;

  padding:
    6px
    6px
    6px
    24px;

  border-radius:
    30px;

  font-size:
    15px;

  font-weight:
    600;

  cursor:
    pointer;

  transition:
    transform 0.2s ease;
}


.btn-action:hover {

  transform:
    translateY(-2px);
}


/* =========================================
   ACTION ICON
========================================= */

.action-icon {

  width:
    36px;

  height:
    36px;

  border-radius:
    50%;

  background:
    rgba(
      0,
      0,
      0,
      0.1
    );

  display:
    flex;

  align-items:
    center;

  justify-content:
    center;
}


.action-icon svg {

  width:
    16px;

  height:
    16px;

  stroke:
    #0f172a;
}


/* =========================================
   VERTICAL SLIDER
========================================= */

.vertical-slider-nav {

  position:
    absolute;

  right:
    48px;

  top:
    50%;

  transform:
    translateY(-50%);

  z-index:
    6;

  display:
    flex;

  flex-direction:
    column;

  align-items:
    center;

  gap:
    12px;

  color:
    rgba(
      255,
      255,
      255,
      0.7
    );

  font-size:
    12px;
}


/* =========================================
   NUMBER BUTTONS
========================================= */

.slider-number-button {

  padding:
    0;

  border:
    none;

  background:
    transparent;

  color:
    rgba(
      255,
      255,
      255,
      0.7
    );

  font-family:
    inherit;

  font-size:
    12px;

  cursor:
    pointer;
}


/* =========================================
   SLIDER TRACK
========================================= */

.slider-track {

  width:
    2px;

  height:
    100px;

  background:
    rgba(
      255,
      255,
      255,
      0.2
    );

  position:
    relative;

  border-radius:
    2px;

  overflow:
    hidden;

  cursor:
    pointer;
}


/* =========================================
   SLIDER PROGRESS
========================================= */

.slider-thumb {

  width:
    100%;

  background:
    #a3e635;

  position:
    absolute;

  top:
    0;

  left:
    0;

  border-radius:
    2px;

  transition:
    height 0.5s ease;
}


/* =========================================
   SLIDE DOTS
========================================= */

.hero-dots {

  position:
    absolute;

  right:
    48px;

  bottom:
    130px;

  z-index:
    7;

  display:
    flex;

  align-items:
    center;

  gap:
    6px;
}


.hero-dot {

  width:
    6px;

  height:
    6px;

  padding:
    0;

  border:
    none;

  border-radius:
    20px;

  background:
    rgba(
      255,
      255,
      255,
      0.45
    );

  cursor:
    pointer;

  transition:
    width 0.3s ease,
    background 0.3s ease;
}


.hero-dot.active {

  width:
    22px;

  background:
    #a3e635;
}


/* =========================================
   BOTTOM TABS
========================================= */

.bottom-tabs-bar {

  position:
    absolute;

  bottom:
    32px;

  left:
    64px;

  right:
    64px;

  z-index:
    6;

  display:
    flex;

  gap:
    16px;
}


/* =========================================
   TAB ITEM
========================================= */

.tab-item {

  flex:
    1;

  display:
    flex;

  flex-direction:
    column;

  justify-content:
    center;

  gap:
    5px;

  background:
    rgba(
      255,
      255,
      255,
      0.2
    );

  backdrop-filter:
    blur(16px);

  -webkit-backdrop-filter:
    blur(16px);

  border:
    1px
    solid
    rgba(
      255,
      255,
      255,
      0.2
    );

  border-radius:
    16px;

  padding:
    10px
    25px;

  min-height:
    72px;

  color:
    rgba(
      255,
      255,
      255,
      0.7
    );

  text-align:
    left;

  cursor:
    default;

  transition:
    background 0.3s ease,
    color 0.3s ease,
    border-color 0.3s ease,
    transform 0.3s ease;
}


/* =========================================
   TAB HOVER
========================================= */

.tab-item:hover {

  background:
    rgba(
      255,
      255,
      255,
      0.3
    );

  color:
    #ffffff;

  transform:
    translateY(-2px);
}


/* =========================================
   DISABLED TAB
========================================= */

.tab-item:disabled {

  opacity:
    1;

  cursor:
    default;
}


/* =========================================
   ACTIVE TAB
========================================= */

.tab-item.active {

  background:
    rgba(
      255,
      255,
      255,
      0.24
    );

  color:
    #ffffff;

  border-color:
    rgba(
      255,
      255,
      255,
      0.32
    );
}


/* =========================================
   TAB LABEL
========================================= */

.tab-label {

  display:
    block;

  font-size:
    12px;

  font-weight:
    700;

  letter-spacing:
    0.8px;

  line-height:
    1.2;
}


/* =========================================
   TAB DETAIL
========================================= */

.tab-detail {

  display:
    block;

  font-size:
    12px;

  font-weight:
    400;

  letter-spacing:
    0;

  line-height:
    1.4;

  opacity:
    0.8;
}


.tab-item.active .tab-detail {

  opacity:
    0.65;
}


/* =========================================
   TABLET
========================================= */

@media (
  max-width: 1100px
) {

  .navbar {

    left:
      32px;

    right:
      32px;
  }


  .navbar.scrolled {

    left:
      0;

    right:
      0;

    padding-left:
      32px;

    padding-right:
      32px;
  }


  .logo-image {

    width:
      135px;
  }


  .hero-section {

    padding:
      0
      40px;
  }


  .bottom-tabs-bar {

    left:
      40px;

    right:
      40px;
  }


  .vertical-slider-nav {

    right:
      32px;
  }


  .hero-dots {

    right:
      32px;
  }

}


/* =========================================
   SMALL TABLET
========================================= */

@media (
  max-width: 900px
) {

  .navbar {

    left:
      24px;

    right:
      24px;
  }


  .navbar.scrolled {

    left:
      0;

    right:
      0;

    padding-left:
      24px;

    padding-right:
      24px;
  }


  .nav-links {

    display:
      none;
  }


  .hero-section {

    padding:
      0
      24px;
  }


  .hero-title {

    font-size:
      clamp(
        36px,
        7vw,
        52px
      );
  }


  .bottom-tabs-bar {

    left:
      24px;

    right:
      24px;

    flex-direction:
      column;

    gap:
      8px;
  }


  .tab-item {

    min-height:
      auto;

    padding:
      10px;
  }


  .hero-dots {

    bottom:
      245px;
  }

}


/* =========================================
   MOBILE
========================================= */

@media (
  max-width: 600px
) {

  .hero-wrapper {

    padding:
      8px;
  }


  .hero-section {

    height:
      calc(
        100vh - 16px
      );

    min-height:
      620px;

    border-radius:
      18px;

    padding:
      0
      20px;
  }


  /* NORMAL HERO NAV */

  .navbar {

    top:
      22px;

    left:
      20px;

    right:
      20px;
  }


  /* SCROLLED HEADER */

  .navbar.scrolled {

    top:
      0;

    left:
      0;

    right:
      0;

    padding:
      9px
      20px;
  }


  .logo-image {

    width:
      115px;
  }


  .btn-primary {

    padding:
      10px
      16px;

    font-size:
      12px;
  }


  .icon-btn {

    width:
      38px;

    height:
      38px;
  }


  .hero-content {

    max-width:
      90%;
  }


  .hero-title {

    font-size:
      clamp(
        34px,
        10vw,
        46px
      );

    margin-bottom:
      28px;
  }


  .title-line {

    width:
      50px;
  }


  .vertical-slider-nav {

    right:
      20px;
  }


  .hero-dots {

    right:
      20px;

    bottom:
      240px;
  }


  .bottom-tabs-bar {

    bottom:
      20px;

    left:
      20px;

    right:
      20px;
  }


  .tab-item {

    padding:
      10px;

    border-radius:
      12px;
  }


  .tab-label {

    font-size:
      10px;
  }


  .tab-detail {

    font-size:
      10px;
  }

}


/* =========================================
   VERY SMALL MOBILE
========================================= */

@media (
  max-width: 420px
) {

  .btn-primary {

    display:
      none;
  }


  .navbar {

    left:
      16px;

    right:
      16px;
  }


  .navbar.scrolled {

    left:
      0;

    right:
      0;

    padding-left:
      16px;

    padding-right:
      16px;
  }


  .hero-section {

    padding:
      0
      16px;
  }


  .bottom-tabs-bar {

    left:
      16px;

    right:
      16px;
  }


  .vertical-slider-nav {

    right:
      16px;
  }


  .hero-dots {

    right:
      16px;
  }

}

</style>