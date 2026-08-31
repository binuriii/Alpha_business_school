
<script setup>
import { computed } from 'vue'

const partnerLogos = [
  {
    id: 1,
    name: 'ACCA Gold Approved Learning Partner',
    image: 'images/image1.jpg'
  },
  {
    id: 2,
    name: 'CFA Society Sri Lanka Candidate Resource Partner',
    image: 'images/image2.jpg'
  },
  {
    id: 3,
    name: 'Financial Modeling Institute',
    image: 'images/image3.jpg'
  },
  {
    id: 4,
    name: 'CIA Certified Internal Auditor',
    image: 'images/image4.jpg'
  },
  {
    id: 5,
    name: 'CAIA Association',
    image: 'images/image5.jpg'
  },
  {
    id: 6,
    name: 'ACCA Licensed CBE Centre',
    image: 'images/image6.jpg'
  },
  {
    id: 7,
    name: 'Metropolitan University',
    image: 'images/image7.jpeg'
  },
  {
    id: 8,
    name: 'Concordia International University',
    image: 'images/image8.jpg'
  },
  {
    id: 9,
    name: 'Empowered by Kaplan',
    image: 'images/image9.jpg'
  },
  {
    id: 10,
    name: 'ACCA Approved Employer Professional Development',
    image: 'images/image10.jpg'
  }
]

const marqueeLogos = computed(() => [...partnerLogos, ...partnerLogos])
</script>

<template>
  <section class="partners-marquee-section">

    <div class="marquee-viewport">
      <div class="marquee-track">
        <div
          v-for="(logo, index) in marqueeLogos"
          :key="`${logo.id}-${index}`"
          class="logo-card"
        >
          <img
            :src="logo.image"
            :alt="logo.name"
          />
        </div>
      </div>
    </div>

  </section>
</template>

<style scoped>
.partners-marquee-section {
  width: 100%;
  background: #ffffff;
  border-radius: 12px;
  padding: 0;
  box-sizing: border-box;
  margin-bottom: 80px;
  overflow: hidden;
  font-family: 'Oakes Grotesk', 'Urbanist', -apple-system,
    BlinkMacSystemFont, sans-serif;
}

.marquee-viewport {
  width: 100%;
  overflow: hidden;
  padding: 10px 0;
  position: relative;

  mask-image: linear-gradient(
    to right,
    transparent,
    black 10%,
    black 90%,
    transparent
  );

  -webkit-mask-image: linear-gradient(
    to right,
    transparent,
    black 10%,
    black 90%,
    transparent
  );
}

.marquee-track {
  display: flex;
  align-items: center;
  gap: 24px;
  width: max-content;
  animation: marquee-scroll 25s linear infinite;
}

.marquee-viewport:hover .marquee-track {
  animation-play-state: paused;
}

@keyframes marquee-scroll {
  0% {
    transform: translateX(0);
  }

  100% {
    transform: translateX(-50%);
  }
}

.logo-card {
  flex: 0 0 180px;
  height: 120px;
  background: #ffffff;
  border-radius: 16px;
  padding: 16px;
  box-sizing: border-box;

  display: flex;
  align-items: center;
  justify-content: center;

  box-shadow: 0 2px 8px rgba(15, 23, 42, 0.04);

  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
}

.logo-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 20px rgba(15, 23, 42, 0.08);
}

.logo-card img {
  max-width: 100%;
  max-height: 100%;
  object-fit: contain;
}

@media (max-width: 900px) {
  .logo-card {
    flex: 0 0 150px;
    height: 100px;
    padding: 12px;
  }
}

@media (max-width: 640px) {
  .logo-card {
    flex: 0 0 130px;
    height: 90px;
    padding: 10px;
  }
}
</style>
```
