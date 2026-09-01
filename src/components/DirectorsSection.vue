<script setup>
import { ref } from 'vue'

const directors = ref([
  {
    id: 1,
    name: 'Dr. Shaan Jayasekera',
    position: 'Chairman',
    qualifications:
      'PhD | MBA (Bus Fin) | BA (Hons) | CIMA Passed Finalist | ACIM | Dip.M',
    image: 'images/director1.jpg'
  },
  {
    id: 2,
    name: 'Shehan Fernando',
    position: 'CEO',
    qualifications:
      'FCCA | CIMA Passed Finalist | BBA (Bus. Econ. - 1st Class) | B.Sc (Applied Accounting)',
    image: 'images/director2.jpg'
  },
  {
    id: 3,
    name: 'Dr. Prasenna Balachandran',
    position: 'Non-Executive Director',
    qualifications:
      'FCCA | CMA | AAT | BSc (Hons) | MIRM (UK)',
    image: 'images/director3.jpg'
  },
  {
    id: 4,
    name: 'Richardson Morais',
    position: 'Nominated Director',
    qualifications:
      'B.Sc (Hons) Applied Accounting | ACCA Affiliate | AAT Passed Finalist',
    image: 'images/director4.jpg'
  }
])
</script>

<template>
  <section class="directors-section">
    <div class="directors-container">

      <!-- HEADER -->
      <div class="directors-header">
        <h2>
          Building a Legacy
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
          <div class="director-image-wrap">
            <img
              :src="director.image"
              :alt="director.name"
              class="director-photo"
              loading="lazy"
            />
          </div>

          <!-- CONTENT -->
          <div class="director-content">

            <h3 class="director-name">
              {{ director.name }}
            </h3>

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
========================================= */

.directors-section {
  width: 100%;
  max-width: 100%;

  padding: 5% 3%;

  margin-top: clamp(12px, 2vh, 24px);

  background: #ffffff;

  box-sizing: border-box;

  font-family:
    'Oakes Grotesk',
    'Urbanist',
    -apple-system,
    BlinkMacSystemFont,
    sans-serif;

  overflow: hidden;
}


/* =========================================
   CONTAINER
========================================= */

.directors-container {
  width: 100%;

  max-width: clamp(1000px, 82vw, 1180px);

  margin: 0 auto;
}


/* =========================================
   HEADER
========================================= */

.directors-header {
  width: 100%;

  max-width: clamp(560px, 52vw, 720px);

  margin:
    0 auto
    clamp(38px, 5vh, 58px);

  text-align: center;
}


.directors-header h2 {
  margin:
    0 0
    clamp(10px, 1.5vh, 18px);

  font-size: clamp(22px, 2.2vw, 36px);

  font-weight: 600;

  line-height: 1.2;

  color: #0f172a;

  font-family: inherit;
}


.directors-header h2 em {
  font-style: italic;

  font-weight: 400;

  color: #0f172a;
}


.directors-header p {
  max-width: 650px;

  margin: 0 auto;

  font-size: clamp(12px, 0.9vw, 15px);

  line-height: 1.5;

  color: #64748b;
}


/* =========================================
   GRID
========================================= */

.directors-grid {
  width: 100%;

  display: grid;

  grid-template-columns:
    repeat(4, minmax(0, 1fr));

  gap: clamp(20px, 2vw, 32px);
}


/* =========================================
   CARD
   (background, border, shadow, padding —
   the whole director sits inside a real card.
   --card-radius / --card-pad are shared with
   the image so the photo can bleed flush to
   the card's outer edges.)
========================================= */

.director-card {
  min-width: 0;

  display: flex;

  flex-direction: column;

  background: #080808;

  border: 1px solid #e2e8f0;

  --card-radius: clamp(16px, 1.6vw, 22px);
  --card-pad: clamp(14px, 1.4vw, 20px);

  border-radius: var(--card-radius);

  padding: var(--card-pad);

  overflow: hidden;

  box-shadow:
    0 4px 14px rgba(15, 23, 42, 0.05);

  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease,
    border-color 0.3s ease;
}


.director-card:hover {
  transform: translateY(-6px);

  border-color: #cbd5e1;

  box-shadow:
    0 20px 44px rgba(15, 23, 42, 0.12);
}


/* =========================================
   IMAGE AREA
   Bleeds past the card's own padding on the
   top/left/right so the photo touches the
   card's rounded top corners and fills the
   full width — no gaps.
========================================= */

.director-image-wrap {
  position: relative;

  width: calc(100% + (2 * var(--card-pad)));

  height: clamp(190px, 20vw, 250px);

  margin:
    calc(-1 * var(--card-pad))
    calc(-1 * var(--card-pad))
    0;

  overflow: hidden;

  background: #1a1a1a;
}


/* =========================================
   ALL DIRECTOR PHOTOS
   SAME SIZE — cover fills the box completely,
   cropping instead of shrinking to fit.
========================================= */

.director-photo {
  width: 100%;

  height: 100%;

  display: block;

  object-fit: cover;

  object-position: center 20%;

  transform: scale(1);

  transform-origin: center center;

  transition: transform 0.4s ease;
}


.director-card:hover .director-photo {
  transform: scale(1.06);
}


/* =========================================
   CONTENT
========================================= */

.director-content {
  padding-top: clamp(14px, 1.4vh, 18px);
}


/* =========================================
   NAME
========================================= */

.director-name {
  margin:
    0 0
    clamp(4px, 0.5vh, 7px);

  font-size: clamp(15px, 1.05vw, 18px);

  font-weight: 600;

  line-height: 1.25;

  color: #ffffff;

  font-family: inherit;
}


/* =========================================
   POSITION
========================================= */

.director-position {
  display: block;

  margin-bottom: clamp(5px, 0.7vh, 8px);

  font-size: clamp(9px, 0.68vw, 11px);

  font-weight: 700;

  line-height: 1.3;

  letter-spacing: 0.5px;

  text-transform: uppercase;

  color: #dbdbdc;
}


/* =========================================
   QUALIFICATIONS
========================================= */

.director-qualifications {
  margin: 0;

  font-size: clamp(10px, 0.75vw, 12px);

  font-weight: 400;

  line-height: 1.55;

  color: #cfd3d8;
}


/* =========================================
   TABLET
========================================= */

@media (max-width: 900px) {

  .directors-container {
    max-width: 100%;
  }

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
      clamp(22px, 4vh, 32px)
      clamp(16px, 3vw, 24px);
  }

  .director-image-wrap {
    height: clamp(200px, 26vw, 260px);
  }
}


/* =========================================
   MOBILE
========================================= */

@media (max-width: 640px) {

  .directors-section {
    padding: 10% 5%;
  }

  .directors-header {
    margin-bottom: clamp(28px, 5vh, 38px);
  }

  .directors-grid {
    grid-template-columns: 1fr;

    gap: clamp(20px, 4vh, 28px);
  }

  .director-card {
    max-width: 430px;

    width: 100%;

    margin: 0 auto;

    padding: clamp(14px, 4vw, 18px);
  }

  .director-image-wrap {
    height: clamp(220px, 60vw, 300px);
  }

  .director-name {
    font-size: clamp(17px, 4.8vw, 20px);
  }

  .director-position {
    font-size: clamp(10px, 3vw, 12px);
  }

  .director-qualifications {
    font-size: clamp(11px, 3.3vw, 13px);
  }
}

</style>