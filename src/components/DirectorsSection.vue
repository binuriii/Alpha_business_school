<script setup>
import { ref } from 'vue'

const directors = ref([
  {
    id: 1,
    name: 'Dr. Shaan Jayasekera',
    position: 'Chairman',
    qualifications:
      'PhD | MBA (Bus Fin) | BA (Hons) | CIMA Passed Finalist | ACIM | Dip.M',
    image: 'images/director1.jpg',
    isLogo: false
  },
  {
    id: 2,
    name: 'Shehan Fernando',
    position: 'CEO',
    qualifications:
      'FCCA | CIMA Passed Finalist | BBA (Bus. Econ. - 1st Class) | B.Sc (Applied Accounting)',
    image: 'images/director2.jpg',
    isLogo: false
  },
  {
    id: 3,
    name: 'Dr. Prasenna Balachandran',
    position: 'Non-Executive Director',
    qualifications:
      'FCCA | CMA | AAT | BSc (Hons) | MIRM (UK)',
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

      <!-- HEADER -->
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
          <div
            class="director-image-wrap"
            :class="{ 'logo-card': director.isLogo }"
          >
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

  margin-top:
    clamp(12px, 2vh, 24px);

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

  /*
    Slightly narrower than before.
    This stops the portraits becoming
    too large on wide desktop screens.
  */
  max-width:
    clamp(1000px, 82vw, 1180px);

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
    0 auto
    clamp(38px, 5vh, 58px);

  text-align: center;
}


.directors-header h2 {
  margin:
    0 0
    clamp(10px, 1.5vh, 18px);

  font-size:
    clamp(22px, 2.2vw, 36px);

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

  font-size:
    clamp(12px, 0.9vw, 15px);

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

  gap:
    clamp(24px, 2.5vw, 42px);
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
    translateY(-0.4vh);
}


/* =========================================
   IMAGE AREA

   REDUCED HEIGHT
========================================= */

.director-image-wrap {
  position: relative;

  width: 100%;

  /*
    Previously:
    clamp(300px, 42vh, 420px)

    Now significantly smaller.
  */
  height:
    clamp(230px, 29vw, 310px);

  display: flex;

  align-items: flex-end;
  justify-content: center;

  background: #ffffff;

  border-radius:
    clamp(10px, 1.2vw, 16px);

  overflow: hidden;

  box-sizing: border-box;
}


/* =========================================
   PEOPLE

   IMPORTANT:
   contain + scale keeps people smaller
   instead of zooming them into the card.
========================================= */

.director-photo {
  width: 100%;
  height: 100%;

  display: block;

  object-fit: contain;
  object-position: center bottom;

  /*
    Makes the person visually smaller.
  */
  transform: scale(0.90);

  transform-origin: center bottom;

  transition:
    transform 0.35s ease;
}


/* subtle hover — don't over-enlarge */
.director-card:hover
.director-photo {
  transform: scale(0.94);
}


/* =========================================
   LOGO CARD
========================================= */

.director-image-wrap.logo-card {
  align-items: center;
  justify-content: center;

  padding:
    clamp(28px, 3vw, 48px);

  background: #ffffff;
}


.director-image-wrap.logo-card
.director-photo {
  width: 100%;
  height: 100%;

  object-fit: contain;
  object-position: center;

  transform: scale(0.82);

  transform-origin: center;
}


.director-card:hover
.director-image-wrap.logo-card
.director-photo {
  transform: scale(0.86);
}


/* =========================================
   CONTENT
========================================= */

.director-content {
  padding-top:
    clamp(10px, 1.3vh, 15px);
}


/* =========================================
   NAME
========================================= */

.director-name {
  margin:
    0 0
    clamp(4px, 0.5vh, 7px);

  font-size:
    clamp(15px, 1.05vw, 18px);

  font-weight: 600;

  line-height: 1.25;

  color: #0f172a;

  font-family: inherit;
}


/* =========================================
   POSITION
========================================= */

.director-position {
  display: block;

  margin-bottom:
    clamp(5px, 0.7vh, 8px);

  font-size:
    clamp(9px, 0.68vw, 11px);

  font-weight: 700;

  line-height: 1.3;

  letter-spacing: 0.5px;

  text-transform: uppercase;

  color: #0f172a;
}


/* =========================================
   QUALIFICATIONS
========================================= */

.director-qualifications {
  margin: 0;

  font-size:
    clamp(10px, 0.75vw, 12px);

  font-weight: 400;

  line-height: 1.55;

  color: #64748b;
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
      clamp(30px, 5vh, 44px)
      clamp(16px, 3vw, 28px);
  }


  .director-image-wrap {
    height:
      clamp(250px, 36vw, 330px);
  }


  .director-photo {
    transform: scale(0.92);
  }


  .director-card:hover
  .director-photo {
    transform: scale(0.96);
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
    margin-bottom:
      clamp(28px, 5vh, 38px);
  }


  .directors-grid {
    grid-template-columns: 1fr;

    gap:
      clamp(34px, 6vh, 48px);
  }


  .director-card {
    max-width: 430px;

    width: 100%;

    margin: 0 auto;
  }


  .director-image-wrap {
    height:
      clamp(270px, 80vw, 360px);
  }


  .director-photo {
    transform: scale(0.92);
  }


  .director-card:hover
  .director-photo {
    transform: scale(0.95);
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