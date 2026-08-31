<script setup>
import { ref } from 'vue'

const directors = ref([
  {
    id: 1,
    name: 'Dr. Shaan Jayasekera',
    position: 'Chairman',
    qualifications: 'PhD | MBA (Bus Fin) | BA (Hons) | CIMA Passed Finalist | ACIM | Dip.M',
    image: 'images/director1.jpg',
    isLogo: false
  },
  {
    id: 2,
    name: 'Shehan Fernando',
    position: 'CEO',
    qualifications: 'FCCA | CIMA Passed Finalist | BBA (Bus. Econ. - 1st Class) | B.Sc (Applied Accounting)',
    image: 'images/director2.jpg',
    isLogo: false
  },
  {
    id: 3,
    name: 'Dr. Prasenna Balachandran',
    position: 'Non-Executive Director',
    qualifications: 'FCCA | CMA | AAT | BSc (Hons) | MIRM (UK)',
    image: 'images/director3.jpg',
    isLogo: false
  },
  {
    id: 4,
    name: 'AIA Holdings',
    position: 'Nominated Director',
    qualifications: 'From AIA Holdings',
    image: 'images/director4.png',
    isLogo: true
  }
])
</script>

<template>
  <section class="directors-section">
    <div class="directors-container">

      <!-- SECTION HEADER -->
      <div class="directors-header">
        <h2>
          Building a Legacy:
          <em>Meet our Board of Directors</em>
        </h2>

        <p>
          Meet the leadership team guiding Alpha Business School with
          experience, vision and a commitment to developing the next
          generation of business and finance professionals.
        </p>
      </div>

      <!-- DIRECTORS -->
      <div class="directors-grid">
        <article
          v-for="director in directors"
          :key="director.id"
          class="director-card"
        >
          <!-- IMAGE -->
          <a
            :href="director.link"
            class="director-image-wrap"
            :class="{ 'logo-card': director.isLogo }"
            target="_blank"
            rel="noopener noreferrer"
            :aria-label="director.name"
          >
            <img
              :src="director.image"
              :alt="director.name"
              class="director-photo"
              loading="lazy"
            />
          </a>

          <!-- CONTENT -->
          <div class="director-content">
            <a
              :href="director.link"
              target="_blank"
              rel="noopener noreferrer"
              class="director-name"
            >
              {{ director.name }}
            </a>

            <span class="director-position">
              {{ director.position }}
            </span>

            <p class="director-qualifications">
              {{ director.qualifications }}
            </p>
          </div>
        </article>
      </div>

    </div>
  </section>
</template>

<style scoped>

/* =========================================
   SECTION
   SAME THEME AS WHY ALPHA
========================================= */

.directors-section {
  width: 100vw;
  max-width: 100%;

  background: #ffffff;

  border-radius:
    clamp(8px, 1.2vw, 16px);

  padding: 5% 3% 5% 3%;

  margin-top:
    clamp(12px, 2vh, 24px);

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
   CONTAINER
========================================= */

.directors-container {
  width: 100%;
  max-width: 1240px;

  margin: 0 auto;
}


/* =========================================
   HEADER
========================================= */

.directors-header {
  width: 100%;

  max-width:
    clamp(560px, 52vw, 720px);

  margin:
    0
    auto
    clamp(35px, 5vh, 58px);

  text-align: center;
}


.directors-header h2 {
  margin:
    0
    0
    clamp(10px, 1.5vh, 18px)
    0;

  font-size:
    clamp(22px, 2.2vw, 36px);

  font-weight: 600;

  color: #0f172a;

  line-height: 1.2;

  font-family: inherit;
}


.directors-header h2 em {
  font-style: italic;
  font-weight: 400;

  color: #0f172a;
}


.directors-header p {
  margin: 0 auto;

  max-width: 650px;

  font-size:
    clamp(12px, 0.9vw, 15px);

  line-height: 1.5;

  color: #64748b;

  font-family: inherit;
}


/* =========================================
   GRID
========================================= */

.directors-grid {
  width: 100%;

  display: grid;

  grid-template-columns:
    repeat(4, minmax(0, 1fr));

  gap:
    clamp(22px, 10vw, 54px);
}


/* =========================================
   CARD
========================================= */

.director-card {
  min-width: 0;

  display: flex;
  flex-direction: column;
  transition:
    transform 0.3s ease;
}


.director-card:hover {
  transform:
    translateY(-0.5vh);
}


/* =========================================
   IMAGE WRAPPER
========================================= */

.director-image-wrap {
  position: relative;

  width: 100%;

  height:
    clamp(300px, 42vh, 420px);

  display: block;

  background: #ffffff;

  border-radius:
    clamp(12px, 1.5vw, 20px);

  overflow: hidden;

  text-decoration: none;
}


/* =========================================
   DIRECTOR PHOTOS
   FORCE IMAGE TO COVER THE WHOLE CARD
========================================= */

.director-photo {
  position: absolute;

  inset: 0;

  width: 100%;
  height: 100%;

  display: block;

  object-fit: cover;
  object-position: center top;

  transform: scale(1.08);

  transition:
    transform 0.35s ease;
}


.director-card:hover
.director-photo {
  transform: scale(1.12);
}


/* =========================================
   AIA LOGO CARD
   LOGOS SHOULD NOT BE CROPPED
========================================= */

.director-image-wrap.logo-card {
  display: flex;

  align-items: center;
  justify-content: center;

  padding:
    clamp(22px, 2.5vw, 38px);

  box-sizing: border-box;

  background: #ffffff;
}


.director-image-wrap.logo-card
.director-photo {
  position: static;

  width: 100%;
  height: 100%;

  object-fit: contain;
  object-position: center;

  transform: none;
}


.director-card:hover
.director-image-wrap.logo-card
.director-photo {
  transform: scale(1.03);
}


/* =========================================
   REMOVE ANY OLD ARROWS / CUTOUTS
========================================= */

.director-arrow,
.director-card-arrow,
.card-arrow,
.corner-cutout,
.director-link-arrow {
  display: none !important;
}


.director-card::before,
.director-card::after,
.director-image-wrap::before,
.director-image-wrap::after {
  content: none !important;

  display: none !important;
}


/* =========================================
   CONTENT
========================================= */

.director-content {
  padding-top:
    clamp(10px, 1.5vh, 16px);
}


/* =========================================
   NAME
========================================= */

.director-name {
  display: inline-block;

  margin:
    0
    0
    clamp(5px, 0.6vh, 8px);

  font-size:
    clamp(15px, 1.1vw, 19px);

  font-weight: 600;

  line-height: 1.25;

  color: #0f172a;

  text-decoration: none;

  font-family: inherit;

  transition:
    opacity 0.2s ease;
}


.director-name:hover {
  opacity: 0.65;
}


/* =========================================
   POSITION
========================================= */

.director-position {
  display: block;

  margin-bottom:
    clamp(6px, 0.8vh, 9px);

  font-size:
    clamp(10px, 0.75vw, 12px);

  font-weight: 700;

  line-height: 1.3;

  letter-spacing: 0.5px;

  text-transform: uppercase;

  color: #0f172a;

  font-family: inherit;
}


/* =========================================
   QUALIFICATIONS
   SINGLE LINE / WRAPPED WITH | SEPARATORS
========================================= */

.director-qualifications {
  margin: 0;

  font-size:
    clamp(11px, 0.8vw, 13px);

  font-weight: 400;

  line-height: 1.55;

  color: #64748b;

  font-family: inherit;
}


/* =========================================
   TABLET
========================================= */

@media (max-width: 900px) {

  .directors-header {
    max-width: 100%;

    margin-left: 0;
    margin-right: 0;

    text-align: left;
  }


  .directors-header p {
    margin-left: 0;

    max-width: 650px;
  }


  .directors-grid {
    grid-template-columns:
      repeat(2, minmax(0, 1fr));

    gap:
      clamp(28px, 4vh, 40px)
      clamp(12px, 1.5vw, 24px);
  }


  .director-image-wrap {
    height:
      clamp(280px, 40vh, 360px);
  }

}


/* =========================================
   MOBILE
========================================= */

@media (max-width: 640px) {

  .directors-header {
    margin-bottom:
      clamp(28px, 4vh, 36px);
  }


  .directors-grid {
    grid-template-columns: 1fr;

    gap:
      clamp(30px, 5vh, 42px);
  }


  .director-image-wrap {
    height:
      clamp(320px, 52vh, 440px);
  }


  .director-name {
    font-size:
      clamp(17px, 4.8vw, 20px);
  }


  .director-position {
    font-size:
      clamp(10px, 3vw, 12px);
  }


  .director-qualifications {
    font-size:
      clamp(11px, 3.3vw, 13px);
  }

}

</style>
