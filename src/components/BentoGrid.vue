<script setup>
import { ref } from 'vue'

const activeCards = ref({
  services: false,
  tall: false,
  classrooms: false
})

const toggleCard = (cardKey) => {
  activeCards.value[cardKey] = !activeCards.value[cardKey]
}
</script>

<template>
  <section class="grid">
    <!-- ABOUT CARD -->
    <div class="card about">
      <div class="about-content">
        <small>ABOUT</small>
        <h2>Alpha Business School is the first step<br />towards a brighter<br />future.</h2>
        <p>We inspire, we educate, and we shape the future!</p>
      </div>
      <img
        src="https://images.unsplash.com/photo-1571260899304-425eee4c7efc?q=80&w=2070&auto=format&fit=crop"
        alt="Students walking together"
      />
    </div>

    <!-- SERVICES / ATHLETICS CARD -->
    <div 
      class="card image-card services" 
      :class="{ 'show-text': activeCards.services }"
    >
      <button class="toggle-btn" @click="toggleCard('services')">
        {{ activeCards.services ? '×' : '+' }}
      </button>

      <template v-if="!activeCards.services">
        <img
          src="https://images.unsplash.com/photo-1663876065260-1f06695da535?w=900&auto=format&fit=crop&q=60&ixlib=rb-4.1.0"
          alt="School pool"
        />
        <div class="dark-overlay"></div>
        <h2>A source of health,<br />strength and athletic<br />achievement.</h2>
      </template>

      <div class="text-view" v-else>
        <small>ATHLETICS</small>
        <h3>Olympic-Standard Facilities</h3>
        <p>
          We offer professional athletic training with an Olympic-sized heated pool, 
          certified coaches, and sports nutrition planning for all student athletes.
        </p>
      </div>
    </div>

    <!-- TALL CARD / LIBRARY -->
    <div 
      class="card image-card tall" 
      :class="{ 'show-text': activeCards.tall }"
    >
      <button class="toggle-btn" @click="toggleCard('tall')">
        {{ activeCards.tall ? '×' : '+' }}
      </button>

      <template v-if="!activeCards.tall">
        <img
          src="https://plus.unsplash.com/premium_photo-1664300897489-fd98eee64faf?q=80&w=2070&auto=format&fit=crop"
          alt="Library study space"
        />
        <div class="dark-overlay"></div>
        <h2>A place to work<br />quietly on your own<br />and your projects.</h2>
      </template>

      <div class="text-view" v-else>
        <small>LIBRARY & STUDY</small>
        <h3>Quiet Learning Spaces</h3>
        <p>
          Our modern library features quiet study zones, collaborative group rooms, 
          and digital access to over 50,000 online journals and resources for research.
        </p>
      </div>
    </div>

    <!-- CLASSROOMS CARD -->
    <div 
      class="card classrooms" 
      :class="{ 'show-text': activeCards.classrooms }"
    >
      <button class="card-btn" @click="toggleCard('classrooms')">
        {{ activeCards.classrooms ? '×' : '+' }}
      </button>

      <template v-if="!activeCards.classrooms">
        <img
          src="https://images.unsplash.com/photo-1640416639872-93aabd8d91d3?q=80&w=1974&auto=format&fit=crop"
          alt="Modern classroom"
        />
        <div class="classroom-content">
          <small>CLASSROOMS</small>
          <h2>Modern equipment</h2>
          <p>
            The classrooms of our school have been equipped with the latest technology, creating an ideal learning environment for students and teachers.
          </p>
        </div>
      </template>

      <div class="text-view full-width" v-else>
        <small>TECHNOLOGY & LABS</small>
        <h3>Interactive Learning Environments</h3>
        <p>
          Every room includes smart interactive displays, ergonomic seating, and individual charging hubs. 
          Students interact seamlessly with cloud-based learning modules, allowing teachers to deliver adaptive real-time feedback.
        </p>
      </div>
    </div>
  </section>
</template>

<style scoped>
.grid {
  width: 100%;
  padding: 0% 3% 5% 3%;
  display: grid;
  grid-template-columns: 1.35fr 0.8fr 0.85fr;
  grid-template-rows: 240px 240px;
  gap: 16px;
}

.card {
  position: relative;
  overflow: hidden;
  border-radius: 12px;
  background: #ffffff;
  transition: all 0.3s ease;
}

.about {
  grid-column: 1;
  grid-row: 1;
  display: flex;
  background: #f2f4f3;
  padding: 12px;
}

.about-content {
  width: 52%;
  padding: 16px 12px 16px 16px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.about-content small,
.classroom-content small,
.text-view small {
  color: #007906;
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 1px;
}

.about-content h2 {
  margin: 0;
  font-size: 22px;
  line-height: 1.2;
  color: #0f172a;
  font-weight: 700;
}

.about-content p {
  margin: 0;
  color: #64748b;
  font-size: 13px;
  line-height: 1.5;
}

.about img {
  width: 48%;
  height: 100%;
  object-fit: cover;
  border-radius: 10px;
}

.image-card img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease;
}

.image-card:hover img {
  transform: scale(1.04);
}

.dark-overlay {
  position: absolute;
  inset: 0;
  background: linear-gradient(
    to top,
    rgba(10, 15, 12, 0.85) 0%,
    transparent 60%
  );
}

.services {
  grid-column: 2;
  grid-row: 1;
}

.tall {
  grid-column: 3;
  grid-row: 1 / span 2;
}

.classrooms {
  grid-column: 1 / span 2;
  grid-row: 2;
  display: flex;
  background: #f2f4f3;
  padding: 12px;
}

.classrooms img {
  width: 48%;
  height: 100%;
  object-fit: cover;
  border-radius: 10px;
}

.classroom-content {
  width: 52%;
  padding: 16px 24px;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.classroom-content h2 {
  font-size: 22px;
  margin: 6px 0 10px 0;
  color: #0f172a;
  font-weight: 700;
}

.classroom-content p {
  color: #64748b;
  font-size: 13px;
  line-height: 1.5;
  margin: 0;
}

.image-card h2 {
  position: absolute;
  left: 20px;
  bottom: 20px;
  margin: 0;
  color: #ffffff;
  font-size: 20px;
  line-height: 1.2;
  font-weight: 600;
  z-index: 2;
}

.toggle-btn,
.card-btn {
  position: absolute;
  right: 14px;
  top: 14px;
  width: 28px;
  height: 28px;
  border: none;
  border-radius: 50%;
  background: #ffffff;
  color: #007906;
  font-size: 16px;
  font-weight: 700;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  z-index: 10;
  box-shadow: 0 2px 6px rgba(0, 0, 0, 0.15);
  transition: transform 0.3s ease, background 0.2s ease, color 0.2s ease;
}

.toggle-btn:hover,
.card-btn:hover {
  transform: scale(1.1);
  background: #007906;
  color: #ffffff;
}

.card.show-text {
  background: #f2f4f3;
}

.text-view {
  width: 100%;
  height: 100%;
  padding: 24px 20px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  animation: fadeIn 0.3s ease-in-out;
}

.text-view.full-width {
  padding: 24px 32px;
}

.text-view h3 {
  margin: 8px 0;
  color: #0f172a;
  font-size: 20px;
  font-weight: 700;
}

.text-view p {
  margin: 0;
  color: #64748b;
  font-size: 13px;
  line-height: 1.5;
}

@keyframes fadeIn {
  from { opacity: 0; transform: translateY(4px); }
  to { opacity: 1; transform: translateY(0); }
}

@media (max-width: 900px) {
  .grid {
    grid-template-columns: 1fr 1fr;
    grid-template-rows: auto;
  }
  .about { grid-column: 1 / span 2; }
  .services { grid-column: 1; min-height: 220px; }
  .tall { grid-column: 2; grid-row: 2 / span 2; min-height: 450px; }
  .classrooms { grid-column: 1; grid-row: 3; flex-direction: column; }
  .classrooms img, .classroom-content { width: 100%; height: auto; }
}
</style>