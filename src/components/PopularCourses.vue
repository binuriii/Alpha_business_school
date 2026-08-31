<script setup>
import { ref } from 'vue'

const selectedSort = ref('Relevance')
const isDropdownOpen = ref(false)

const sortOptions = [
  'Relevance',
  'Popularity',
  'Rating'
]

const toggleDropdown = () => {
  isDropdownOpen.value = !isDropdownOpen.value
}

const selectSort = (option) => {
  selectedSort.value = option
  isDropdownOpen.value = false
}

const courses = ref([
  {
    id: 1,
    category: 'ACCA',
    flag: 'fi fi-gb',
    badgeText: 'Gold Partner',
    title: 'ACCA (Association of Chartered Certified Accountants)',
    description:
      'Gold Approved Learning Partner offering a globally recognized accounting qualification building expertise in finance, audit, and taxation.',
    lessons: 'Applied Knowledge & Skills',
    type: 'Global Career Path',
    votes: 'Global Standard',
    rating: 5,
    image:
      'https://images.unsplash.com/photo-1621610085626-0ceec4fc7480?q=80&w=2070&auto=format&fit=crop',
    linkUrl: '#'
  },

  {
    id: 2,
    category: 'CFA',
    flag: 'fi fi-us',
    badgeText: 'Candidate Resource Partner',
    title: 'CFA (Chartered Financial Analyst)',
    description:
      "Sri Lanka's only CFA Society Candidate Resource Partner focusing on investment management, ethics, valuation, and financial analysis.",
    lessons: '3 Exam Levels',
    type: 'Investment Focus',
    votes: 'Gold Standard',
    rating: 5,
    image:
      'https://plus.unsplash.com/premium_photo-1661750213430-6760e4c07d75?w=900&auto=format&fit=crop&q=60',
    linkUrl: '#'
  },

  {
    id: 3,
    category: 'CPA Australia',
    flag: 'fi fi-au',
    badgeText: 'Registered Provider',
    title: 'CPA Australia Qualification',
    description:
      "Sri Lanka's only REGISTERED Tuition Provider for CPA Australia. A preferred qualification for skilled migration and global business roles.",
    lessons: 'CPA Program',
    type: 'Skilled Migration',
    votes: 'Top Recognized',
    rating: 5,
    image:
      'https://images.unsplash.com/photo-1519810410960-332413a4e48f?w=900&auto=format&fit=crop&q=60',
    linkUrl: '#'
  },

  {
    id: 4,
    category: 'AFM',
    flag: 'fi fi-ca',
    badgeText: 'Financial Modeling',
    title: 'AFM - Advanced Financial Modeler',
    description:
      "Sri Lanka's only AFM Provider by FMI. Focuses on practical financial modeling, corporate finance, valuation, and business decision-making.",
    lessons: 'Practical Modeling',
    type: 'Valuation & Finance',
    votes: 'FMI Certified',
    rating: 5,
    image:
      'https://plus.unsplash.com/premium_photo-1661378451904-75b44d55a216?w=900&auto=format&fit=crop&q=60',
    linkUrl: '#'
  },

  {
    id: 5,
    category: 'CIA',
    flag: 'fi fi-us',
    badgeText: 'Internal Auditor',
    title: 'CIA (Certified Internal Auditor)',
    description:
      'Globally recognized credential offered by IIA focused on internal auditing, risk management, governance, and internal controls.',
    lessons: '3 Core Parts',
    type: 'Governance & Audit',
    votes: 'IIA Credential',
    rating: 5,
    image:
      'https://images.unsplash.com/photo-1598466932807-0751a2bb369a?w=900&auto=format&fit=crop&q=60',
    linkUrl: '#'
  },

  {
    id: 6,
    category: 'FRM',
    flag: 'fi fi-us',
    badgeText: 'Risk Manager',
    title: 'FRM (Financial Risk Manager)',
    description:
      'Offered by GARP, the global benchmark for risk management widely recognized by banking and financial institutions worldwide.',
    lessons: 'Part I & Part II',
    type: 'Risk & Banking',
    votes: 'GARP Benchmark',
    rating: 5,
    image:
      'https://images.unsplash.com/photo-1587614380862-0294308ae58b?w=900&auto=format&fit=crop&q=60',
    linkUrl: '#'
  }
])
</script>

<template>
  <section class="courses-section">

    <!-- ================================
         SECTION HEADER
    ================================= -->

    <div class="courses-header">

      <div class="header-text">

        <h2>Globally Recognized Qualifications</h2>

        <p>
          Empower your career with world-renowned professional programs in
          finance, accounting, risk management, and investment analysis.
        </p>

      </div>

      <!-- SORT DROPDOWN -->

      <div class="sort-wrapper">

        <button
          class="sort-btn"
          @click="toggleDropdown"
        >

          <svg
            class="sort-icon"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
          >
            <path d="M7 15l5 5 5-5M7 9l5-5 5 5" />
          </svg>

          Sort by
          <strong>{{ selectedSort }}</strong>

        </button>

        <div
          v-if="isDropdownOpen"
          class="sort-dropdown"
        >

          <button
            v-for="option in sortOptions"
            :key="option"
            class="dropdown-item"
            :class="{ active: option === selectedSort }"
            @click="selectSort(option)"
          >
            {{ option }}
          </button>

        </div>

      </div>

    </div>

    <div class="courses-grid">

      <div
        v-for="course in courses"
        :key="course.id"
        class="course-card"
      >

        <div class="card-image">

          <img
            :src="course.image"
            :alt="course.title"
          />

        </div>

        <div class="card-body">

          <div class="card-meta">

            <span class="category-tag">

              <span
                class="fi"
                :class="course.flag"
                aria-hidden="true"
              ></span>

              <span class="category-name">
                {{ course.category }}
              </span>

            </span>

            <span class="badge-text">
              {{ course.badgeText }}
            </span>

          </div>


          <!-- TITLE -->

          <h3 class="course-title">
            {{ course.title }}
          </h3>


          <!-- DESCRIPTION -->

          <p class="course-desc">
            {{ course.description }}
          </p>


          <!-- DETAILS -->

          <div class="details-row">

            <span class="detail-item green">
              {{ course.lessons }}
            </span>

            <span class="detail-item slate">
              {{ course.type }}
            </span>

          </div>


          <!-- DIVIDER -->

          <div class="card-divider"></div>


          <!-- FOOTER -->

          <div class="card-footer">

            <div class="rating-box">

              <span class="stars">
                ★★★★★
              </span>

              <span class="votes">
                {{ course.votes }}
              </span>

            </div>


            <!-- 45 DEGREE ARROW -->

            <a
              :href="course.linkUrl"
              class="action-btn"
              :aria-label="`View ${course.title} program`"
            >

              <svg
                viewBox="0 0 24 24"
                fill="none"
                stroke="currentColor"
                stroke-width="2.5"
              >
                <path d="M7 17L17 7M17 7H7M17 7V17" />
              </svg>

            </a>

          </div>

        </div>

      </div>

    </div>

  </section>
</template>


<style scoped>

.courses-section {
  width: 100vw;
  max-width: 100%;
  background: #f5f4f0;
  border-radius: clamp(8px, 1.2vw, 16px);
  padding: 5% 3%;
  margin-top: clamp(12px, 2vh, 24px);
  box-sizing: border-box;

  font-family:
    'Oakes Grotesk',
    'Urbanist',
    -apple-system,
    BlinkMacSystemFont,
    sans-serif;
}

.courses-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;

  gap: clamp(20px, 3.5vw, 48px);

  margin-bottom: clamp(24px, 4.5vh, 56px);
}

.header-text {
  flex: 1;
}

.header-text h2 {
  margin: 0 0 clamp(8px, 1vh, 16px);

  font-size: clamp(22px, 2.2vw, 36px);

  font-weight: 600;

  color: #0f172a;

  line-height: 1.2;

  font-family: inherit;
}

.header-text p {
  margin: 0;

  font-size: clamp(12px, 0.9vw, 15px);

  line-height: 1.5;

  color: #64748b;

  max-width: clamp(320px, 40vw, 580px);

  font-family: inherit;
}

.sort-wrapper {
  position: relative;
  flex-shrink: 0;
}

.sort-btn {
  display: flex;
  align-items: center;

  gap: clamp(6px, 0.6vw, 10px);

  background: #ffffff;

  border: 1px solid #cbd5e1;

  padding:
    clamp(6px, 0.8vh, 10px)
    clamp(12px, 1vw, 20px);

  border-radius: clamp(6px, 0.6vw, 10px);

  font-size: clamp(11px, 0.8vw, 13px);

  color: #475569;

  cursor: pointer;

  box-shadow:
    0 1px 3px rgba(0, 0, 0, 0.04);

  transition: all 0.2s ease;

  font-family: inherit;
}

.sort-btn:hover {
  border-color: #007906;
}

.sort-icon {
  width: clamp(12px, 0.9vw, 16px);
  height: clamp(12px, 0.9vw, 16px);
}

.sort-dropdown {
  position: absolute;

  top: calc(100% + clamp(4px, 0.6vh, 8px));

  right: 0;

  background: #ffffff;

  border: 1px solid #e2e8f0;

  border-radius: clamp(6px, 0.6vw, 10px);

  box-shadow:
    0 10px 15px -3px rgba(0, 0, 0, 0.1);

  width: clamp(140px, 12vw, 190px);

  z-index: 20;

  padding: clamp(3px, 0.4vh, 6px) 0;

  overflow: hidden;
}

.dropdown-item {
  width: 100%;

  text-align: left;

  padding:
    clamp(6px, 0.8vh, 10px)
    clamp(10px, 0.8vw, 14px);

  background: transparent;

  border: none;

  font-size: clamp(11px, 0.8vw, 13px);

  color: #334155;

  cursor: pointer;

  transition: background 0.15s ease;

  font-family: inherit;
}

.dropdown-item:hover,
.dropdown-item.active {
  background: #f1f5f9;

  color: #007906;

  font-weight: 600;
}

.courses-grid {
  display: grid;

  grid-template-columns: repeat(3, 1fr);

  gap: clamp(16px, 1.8vw, 28px);

  padding:
    clamp(6px, 0.8vh, 10px)
    clamp(2px, 0.3vw, 6px)
    clamp(12px, 1.5vh, 20px)
    clamp(2px, 0.3vw, 6px);
}

.course-card {
  background: #ffffff;

  border-radius: clamp(8px, 1vw, 14px);

  padding: clamp(8px, 0.8vw, 14px);

  border: 1px solid rgba(15, 23, 42, 0.08);

  box-shadow:
    0 10px 25px -5px rgba(15, 23, 42, 0.08),
    0 8px 10px -6px rgba(15, 23, 42, 0.04);

  display: flex;
  flex-direction: column;

  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease,
    border-color 0.3s ease;
}

.course-card:hover {
  transform: translateY(-0.6vh);

  box-shadow:
    0 20px 30px -10px rgba(15, 23, 42, 0.16),
    0 10px 15px -5px rgba(15, 23, 42, 0.08);
}

.card-image {
  width: 100%;

  height: clamp(160px, 22vh, 240px);

  border-radius: clamp(6px, 0.6vw, 10px);

  overflow: hidden;

  background: #e2e8f0;
}

.card-image img {
  width: 100%;
  height: 100%;

  object-fit: cover;

  display: block;
}

.card-body {
  padding:
    clamp(12px, 1.5vh, 20px)
    clamp(6px, 0.5vw, 10px)
    clamp(6px, 0.5vw, 10px);

  display: flex;

  flex-direction: column;

  flex: 1;
}

.card-meta {
  display: flex;

  justify-content: space-between;

  align-items: center;

  gap: 8px;

  margin-bottom: clamp(8px, 1vh, 14px);
}

.category-tag {
  display: inline-flex;

  align-items: center;

  gap: 7px;

  font-size: clamp(10px, 0.75vw, 12px);

  color: #ffffff;

  background: #000000;

  padding:
    clamp(3px, 0.3vh, 5px)
    clamp(7px, 0.5vw, 10px);

  border-radius:
    clamp(3px, 0.3vw, 6px);

  font-weight: 600;

  white-space: nowrap;
}

.category-tag .fi {
  display: inline-block;

  width: 16px;

  height: 11px;

  border-radius: 1px;

  flex-shrink: 0;

  background-size: cover;

  background-position: center;
}

.category-name {
  font-weight: 700;
}

.badge-text {
  font-size: clamp(10px, 0.75vw, 12px);

  font-weight: 700;

  color: #007906;

  text-align: right;

  white-space: nowrap;

  overflow: hidden;

  text-overflow: ellipsis;
}

.course-title {
  font-size: clamp(13px, 1vw, 16px);

  font-weight: 700;

  color: #0f172a;

  margin:
    0
    0
    clamp(6px, 0.8vh, 10px);

  line-height: 1.35;

  font-family: inherit;
}


.course-desc {
  font-size: clamp(11px, 0.8vw, 13px);

  line-height: 1.45;

  color: #64748b;

  margin:
    0
    0
    clamp(10px, 1.2vh, 16px);

  display: -webkit-box;

  -webkit-line-clamp: 3;

  line-clamp: 3;

  -webkit-box-orient: vertical;

  overflow: hidden;
}

.details-row {
  display: flex;

  gap: clamp(10px, 1.2vw, 18px);

  margin-top: auto;

  margin-bottom: clamp(10px, 1.2vh, 16px);
}

.detail-item {
  display: flex;

  align-items: center;

  gap: clamp(4px, 0.4vw, 8px);

  font-size: clamp(10px, 0.75vw, 12px);
}

.detail-item.green {
  color: #007906;
}

.detail-item.slate {
  color: #64748b;
}

.card-divider {
  width: 100%;

  height: 1px;

  background: #f1f5f9;

  margin-bottom: clamp(8px, 1vh, 14px);
}

.card-footer {
  display: flex;

  justify-content: space-between;

  align-items: center;
}

.rating-box {
  display: flex;

  align-items: center;

  gap: clamp(4px, 0.4vw, 8px);
}

.stars {
  color: #f59e0b;

  font-size: clamp(10px, 0.8vw, 13px);

  letter-spacing: 1px;
}

.votes {
  font-size: clamp(10px, 0.75vw, 12px);

  color: #94a3b8;
}

.action-btn {
  display: flex;

  align-items: center;

  justify-content: center;

  text-decoration: none;

  background: transparent;

  padding: clamp(3px, 0.4vw, 6px);

  transition: transform 0.2s ease;
}

.action-btn:hover {
  transform: translate(2px, -2px);
}

.action-btn svg {
  width: clamp(16px, 1.3vw, 22px);

  height: clamp(16px, 1.3vw, 22px);

  stroke: #0f172a;
}

@media (max-width: 992px) {

  .courses-grid {
    grid-template-columns: repeat(2, 1fr);
  }

}

@media (max-width: 640px) {

  .courses-header {
    flex-direction: column;

    gap: clamp(12px, 1.8vh, 20px);
  }

  .courses-grid {
    grid-template-columns: 1fr;
  }

  .card-meta {
    align-items: flex-start;
  }

  .badge-text {
    max-width: 45%;
  }

}

</style>