<script setup>
import { ref } from 'vue'

const scrollContainer = ref(null)
const activeIndex = ref(0)

const courseCards = ref([
  {
    id: 1,
    title: 'Accounting & Finance',
    image: 'https://images.unsplash.com/photo-1554224155-3a58922a22c3?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTJ8fEFjY291bnRpbmclMjAlMjYlMjBGaW5hbmNlfGVufDB8fDB8fHww',
    linkUrl: '#'
  },
  {
    id: 2,
    title: 'Business & Management',
    image: 'https://plus.unsplash.com/premium_photo-1661431396990-7bc93ef3edec?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NjR8fEJ1c2luZXNzJTIwJTI2JTIwTWFuYWdlbWVudHxlbnwwfHwwfHx8MA%3D%3D',
    linkUrl: '#'
  },
  {
    id: 3,
    title: 'Auditing & Risk',
    image: 'https://images.unsplash.com/photo-1660020619062-70b16c44bf0f?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDQ1fHx8ZW58MHx8fHx8',
    linkUrl: '#'
  },
  {
    id: 4,
    title: 'Financial Modelling',
    image: 'https://images.unsplash.com/photo-1709534486708-fb8f94150d0a?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTU5fHxBdWRpdGluZyUyMCUyNiUyMFJpc2t8ZW58MHx8MHx8fDA%3D',
    linkUrl: '#'
  },
  {
    id: 5,
    title: 'Professional Qualifications',
    image: 'https://plus.unsplash.com/premium_photo-1661750213430-6760e4c07d75?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDIwfHx8ZW58MHx8fHx8',
    linkUrl: '#'
  }
])

const scrollToCard = (index) => {
  if (!scrollContainer.value) return

  if (index < 0) {
    index = courseCards.value.length - 1
  } else if (index >= courseCards.value.length) {
    index = 0
  }

  const cards = scrollContainer.value.querySelectorAll('.course-card')

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
  <section class="trending-courses-section">

    <!-- SECTION HEADER -->
    <div class="header-container">

      <div class="header-left">
        <h2>
          Explore <em>top-rated</em><br />
          programmes
        </h2>
      </div>

      <div class="header-right">

        <p>
          Gain globally recognised qualifications and industry-focused skills
          in accounting, finance, business, auditing, financial modelling and
          risk management.
        </p>

        <div class="header-actions">
          <a href="#" class="section-link">
            Explore All Programmes

            <svg
              class="header-arrow"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2.5"
            >
              <path d="M7 17L17 7M17 7H7M17 7V17"/>
            </svg>
          </a>
        </div>

      </div>

    </div>


    <!-- =====================================
         CAROUSEL WITH SIDE ARROWS
    ====================================== -->

    <div class="carousel-relative-container">

      <!-- PREVIOUS ARROW -->
      <button
        class="nav-arrow prev-arrow"
        @click="prevSlide"
        aria-label="Previous programme"
      >
        <svg
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2.5"
        >
          <path d="M15 18l-6-6 6-6"/>
        </svg>
      </button>


      <!-- CARDS -->
      <div
        class="carousel-track"
        ref="scrollContainer"
      >

        <div
          v-for="card in courseCards"
          :key="card.id"
          class="course-card"
        >

          <img
            :src="card.image"
            :alt="card.title"
          />

          <!-- CARD BADGE -->
          <div class="card-badge">

            <span class="badge-title">
              {{ card.title }}
            </span>

            <a
              :href="card.linkUrl"
              class="arrow-btn"
              :aria-label="`View details for ${card.title}`"
            >
              <svg
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                stroke-width="2.5"
              >
                <path d="M7 17L17 7M17 7H7M17 7V17"/>
              </svg>
            </a>

          </div>

        </div>

      </div>


      <!-- NEXT ARROW -->
      <button
        class="nav-arrow next-arrow"
        @click="nextSlide"
        aria-label="Next programme"
      >
        <svg
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2.5"
        >
          <path d="M9 18l6-6-6-6"/>
        </svg>
      </button>

    </div>

  </section>
</template>


<style scoped>

/* =========================================
   MAIN SECTION
========================================= */

.trending-courses-section {
  width: 100vw;
  max-width: 100%;

  background: #f5f4f0;

  border-radius: clamp(8px, 1.2vw, 16px);

  padding: 5% 3%;

  margin-top: clamp(12px, 2vh, 24px);

  box-sizing: border-box;

  overflow: hidden;

  font-family:
    'Oakes Grotesk',
    'Urbanist',
    -apple-system,
    BlinkMacSystemFont,
    sans-serif;
}


/* =========================================
   HEADER
========================================= */

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

  font-family: inherit;
}

.header-left h2 em {
  font-style: italic;

  font-weight: 400;
}


/* =========================================
   HEADER RIGHT
========================================= */

.header-right {
  flex: 1;
}

.header-right p {
  margin: 0 0 clamp(12px, 1.8vh, 24px) 0;

  font-size: clamp(12px, 0.9vw, 15px);

  line-height: 1.5;

  color: #64748b;

  font-family: inherit;
}


/* =========================================
   EXPLORE LINK
========================================= */

.header-actions {
  display: flex;

  align-items: center;
}

.section-link {
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

.section-link:hover {
  opacity: 0.75;
}

.header-arrow {
  width: clamp(12px, 1vw, 16px);

  height: clamp(12px, 1vw, 16px);
}


/* =========================================
   CAROUSEL CONTAINER
========================================= */

.carousel-relative-container {
  position: relative;

  width: 100%;
}


/* =========================================
   CAROUSEL TRACK
========================================= */

.carousel-track {
  display: flex;

  gap: clamp(12px, 1.5vw, 24px);

  overflow-x: auto;

  scroll-behavior: smooth;

  scrollbar-width: none;

  padding:
    clamp(3px, 0.4vh, 6px)
    clamp(20px, 2.5vw, 40px)
    clamp(8px, 1.2vh, 16px)
    clamp(20px, 2.5vw, 40px);

  scroll-snap-type: x mandatory;
}

.carousel-track::-webkit-scrollbar {
  display: none;
}


/* =========================================
   COURSE CARD
========================================= */

.course-card {
  position: relative;

  flex: 0 0 calc(
    33.333% - clamp(8px, 1vw, 16px)
  );

  min-width: clamp(220px, 20vw, 280px);

  height: clamp(300px, 42vh, 420px);

  border-radius: clamp(12px, 1.5vw, 20px);

  overflow: hidden;

  scroll-snap-align: start;

  transition:
    transform 0.3s ease;
}

.course-card:hover {
  transform: translateY(-0.5vh);
}


/* =========================================
   IMAGE
========================================= */

.course-card img {
  width: 100%;

  height: 100%;

  object-fit: cover;

  display: block;
}


/* =========================================
   CARD BADGE
========================================= */

.card-badge {
  position: absolute;

  bottom: clamp(10px, 1.5vh, 20px);

  left: clamp(10px, 1.2vw, 20px);

  right: clamp(10px, 1.2vw, 20px);

  background: #000000;

  border-radius: clamp(8px, 1vw, 14px);
  padding:
    clamp(10px, 1.2vh, 16px)
    clamp(12px, 1.2vw, 20px);

  display: flex;

  align-items: center;

  justify-content: space-between;

  box-shadow:
    0 4px 12px rgba(15, 23, 42, 0.08);
}

.badge-title {
  font-size: clamp(12px, 0.95vw, 16px);

  font-weight: 600;

  color: #ffffff;

  font-family: inherit;
}


/* =========================================
   CARD ARROW
========================================= */

.arrow-btn {
  display: flex;

  align-items: center;

  justify-content: center;

  text-decoration: none;

  background: transparent;

  padding: clamp(3px, 0.4vw, 6px);

  transition:
    transform 0.2s ease;
}

.arrow-btn:hover {
  transform: translate(2px, -2px);
}

.arrow-btn svg {
  width: clamp(16px, 1.3vw, 22px);

  height: clamp(16px, 1.3vw, 22px);

  stroke: #ffffff;
}


/* =========================================
   SIDE NAVIGATION
   EXACT CAREER PATHWAYS STYLE
========================================= */

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

  box-shadow:
    0 4px 10px rgba(15, 23, 42, 0.08);

  transition:
    all 0.2s ease;
}


/* LEFT ARROW */

.prev-arrow {
  left: clamp(-20px, -1.2vw, -12px);
}


/* RIGHT ARROW */

.next-arrow {
  right: clamp(-20px, -1.2vw, -12px);
}


/* ARROW ICON */

.nav-arrow svg {
  width: clamp(12px, 1vw, 18px);

  height: clamp(12px, 1vw, 18px);

  stroke: #0f172a;
}


/* HOVER */

.nav-arrow:hover {
  border-color: #0f172a;

  background-color: #f1f5f9;
}


/* =========================================
   TABLET
========================================= */

@media (max-width: 900px) {

  .header-container {
    flex-direction: column;

    gap: clamp(12px, 1.8vh, 20px);
  }

  .header-right {
    width: 100%;
  }

  .course-card {
    flex: 0 0 calc(
      50% - clamp(6px, 0.8vw, 12px)
    );

    height: clamp(260px, 35vh, 340px);
  }

}


/* =========================================
   MOBILE
========================================= */

@media (max-width: 640px) {

  .trending-courses-section {
    padding: 8% 5%;
  }

  .course-card {
    flex: 0 0 85vw;
  }

  .carousel-track {
    padding-left: 5px;

    padding-right: 5px;
  }

  .nav-arrow {
    display: none;
  }

}

</style>