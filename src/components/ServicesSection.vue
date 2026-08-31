<script setup>
import { ref } from 'vue'

const services = ref([
  {
    id: 1,
    title: 'Accounting &\nFinance',
    description: 'Master the knowledge that drives modern businesses and financial decisions.',
    image: 'https://images.unsplash.com/photo-1709534486708-fb8f94150d0a?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NHx8QWNjb3VudGluZyUyMCUyNiUyMEZpbmFuY2UlMjBUYWlsb3JlZCUyMHN0cmF0ZWdpZXMlMjB0byUyMGJ1aWxkJTIwcHJlc2VydmV8ZW58MHx8MHx8fDA%3D',
    iconClass: 'fa-solid fa-chart-pie',
    isHighlighted: false
  },
  {
    id: 2,
    title: 'Professional \nQualifications',
    description: 'Build globally recognized skills for a successful career.',
    image: 'images/student.jpeg',
    iconClass: 'fa-solid fa-file-lines',
    isHighlighted: true
  },
  {
    id: 3,
    title: 'Business & \nManagement',
    description: 'Develop practical skills to lead, manage, and grow in the business world.',
    image: 'https://images.unsplash.com/photo-1781246212288-7fa538344718?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDJ8fHxlbnwwfHx8fHw%3D',
    iconClass: 'fa-solid fa-umbrella',
    isHighlighted: false
  },
  {
    id: 4,
    title: 'Data & Financial \nModelling',
    description: 'Turn numbers into insights and make smarter business decisions.',
    image: 'https://images.unsplash.com/photo-1551288049-bebda4e38f71?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8MTB8fERhdGElMjAlMjYlMjBGaW5hbmNpYWwlMjBNb2RlbGxpbmd8ZW58MHx8MHx8fDA%3D',
    iconClass: 'fa-solid fa-chart-line',
    isHighlighted: false
  }
])
</script>

<template>
  <section class="services-section">
    <div class="services-container">

      <!-- HEADER -->
      <div class="services-header">
        <h2>
          Trending Programmes to <br><em>Shape Your Career</em>
          <br class="desktop-br" />
        </h2>
      </div>

      <!-- SERVICES GRID -->
      <div class="services-grid">

        <div
          v-for="service in services"
          :key="service.id"
          class="service-card"
          :class="{ highlighted: service.isHighlighted }"
        >

          <!-- CARD INFO -->
          <div class="service-card-info">

            <div class="service-card-header">

              <h3 class="service-title">
                {{ service.title }}
              </h3>

              <button
                class="service-action-btn"
                aria-label="Learn more"
              >
                <i class="fa-solid fa-arrow-up-right-from-square"></i>
              </button>

            </div>

            <p class="service-description">
              {{ service.description }}
            </p>

          </div>


          <!-- IMAGE -->
          <div
            class="service-image-wrap"
            :class="{ highlighted: service.isHighlighted }"
          >

            <div
              v-if="service.isHighlighted"
              class="lime-background"
            ></div>

            <img
              :src="service.image"
              :alt="service.title"
              :class="{ 'student-image': service.isHighlighted }"
            />

            <div class="service-floating-icon">
              <i :class="service.iconClass"></i>
            </div>

          </div>

        </div>

      </div>
    </div>
  </section>
</template>

<style scoped>
@import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css');
@import url('https://fonts.googleapis.com/css2?family=Urbanist:ital,wght@0,400;0,500;0,600;0,700;1,400&display=swap');


.services-section {
  width: 100%;
  max-width: 100%;

  background: #f5f4f0;

  padding:
    clamp(32px, 5vh, 64px)
    clamp(16px, 3vw, 32px);

  box-sizing: border-box;
  overflow: hidden;
  border-radius: clamp(8px, 1.2vw, 16px);
  font-family:
    'Oakes Grotesk',
    'Urbanist',
    -apple-system,
    BlinkMacSystemFont,
    sans-serif;
}


.services-container {
  width: 100%;
  max-width: 1240px;

  margin: 0 auto;
}

.services-header {
  text-align: center;

  margin-bottom:
    clamp(24px, 4vh, 48px);
}


.services-header h2 {
  margin: 0;

  font-size:
    clamp(22px, 2.2vw, 36px);

  font-weight: 600;

  color: #0f172a;

  line-height: 1.2;
}


.services-header h2 em {
  font-style: italic;
  font-weight: 400;
}


.desktop-br {
  display: inline;
}


.services-grid {
  display: grid;

  grid-template-columns:
    repeat(4, 1fr);

  gap:
    clamp(16px, 1.8vw, 24px);
}

.service-card {
  position: relative;

  background: #ffffff;

  border-radius:
    clamp(16px, 2vw, 24px);

  padding:
    clamp(16px, 2vh, 24px);

  border: 1px solid #f1f5f9;

  display: flex;
  flex-direction: column;

  justify-content: space-between;

  height: 380px;

  box-sizing: border-box;

  box-shadow:
    0 1px 3px rgba(0, 0, 0, 0.04);

  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
}


.service-card:hover {
  transform: translateY(-4px);

  box-shadow:
    0 10px 25px rgba(0, 0, 0, 0.08);
}

.service-card.highlighted {
  background: #010101;

  border-color: #010101;

  box-shadow:
    0 10px 25px rgba(163, 230, 53, 0.3);
}

.service-card-info {
  display: flex;

  flex-direction: column;

  height: 120px;
}


.service-card-header {
  display: flex;

  justify-content: space-between;

  align-items: flex-start;

  margin-bottom:
    clamp(8px, 1vh, 12px);
}

.service-title {
  margin: 0;

  font-size:
    clamp(15px, 1.2vw, 18px);

  font-weight: 600;

  color: #0f172a;

  line-height: 1.25;

  white-space: pre-line;
}

.service-card.highlighted .service-title {
  color: #ffffff;
}

.service-action-btn {
  width:
    clamp(28px, 2.5vw, 32px);

  height:
    clamp(28px, 2.5vw, 32px);

  border-radius: 50%;

  border: 1px solid #cbd5e1;

  background: #ffffff;

  display: flex;

  align-items: center;
  justify-content: center;

  cursor: pointer;

  flex-shrink: 0;

  color: #0f172a;

  font-size:
    clamp(10px, 0.9vw, 12px);
}


.service-card.highlighted .service-action-btn {
  background: #0f172a;

  border-color: #0f172a;

  color: #ffffff;
}

.service-description {
  margin: 0;

  font-size:
    clamp(12px, 0.9vw, 14px);

  line-height: 1.5;

  color: #64748b;
}

.service-card.highlighted .service-description {
  color: #ffffff;

  font-weight: 500;
}

.service-image-wrap {
  position: relative;

  width: 100%;

  height: 200px;

  border-radius:
    clamp(12px, 1.5vw, 16px);

  overflow: hidden;

  background: #ffffff;
}

.service-image-wrap > img {
  position: absolute;

  inset: 0;

  width: 100%;
  height: 100%;

  display: block;

  object-fit: cover;
}


/* =========================================
   SECOND CARD IMAGE
========================================= */

.service-image-wrap.highlighted {
  background: #a3e635;
}


/* Lime background */

.lime-background {
  position: absolute;

  inset: 0;

  width: 100%;
  height: 100%;

  background: #a3e635;

  z-index: 0;
}


/* =========================================
   STUDENT IMAGE

   CROPPED TO REMOVE THE WHITE BORDER
========================================= */

.service-image-wrap .student-image {
  position: absolute;

  top: -2%;

  left: -8%;

  width: 116%;

  height: 104%;

  max-width: none;

  object-fit: cover;

  display: block;

  z-index: 1;
}


/* =========================================
   FLOATING ICON
========================================= */

.service-floating-icon {
  position: absolute;

  bottom:
    clamp(10px, 1.2vw, 14px);

  left:
    clamp(10px, 1.2vw, 14px);

  width:
    clamp(28px, 2.5vw, 34px);

  height:
    clamp(28px, 2.5vw, 34px);

  border-radius: 50%;

  background: #a3e635;

  color: #0f172a;

  display: flex;

  align-items: center;
  justify-content: center;

  font-size:
    clamp(11px, 0.9vw, 13px);

  box-shadow:
    0 2px 6px rgba(0, 0, 0, 0.15);

  z-index: 5;
}


/* =========================================
   RESPONSIVE
========================================= */

@media (max-width: 1024px) {

  .services-grid {
    grid-template-columns:
      repeat(2, 1fr);
  }

}


@media (max-width: 640px) {

  .services-grid {
    grid-template-columns: 1fr;
  }

  .desktop-br {
    display: none;
  }

}

</style>