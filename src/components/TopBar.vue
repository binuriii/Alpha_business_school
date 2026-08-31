<script setup>
import { ref } from 'vue'

const selectedLanguage = ref('English')

const contact = {
  email: 'info@alphabusiness.lk',
  phoneDisplay: '+94 773 654 254',
  phoneLink: '+94773654254',
  whatsapp: '94773654254'
}

const openWhatsApp = () => {
  window.open(
    `https://wa.me/${contact.whatsapp}`,
    '_blank',
    'noopener,noreferrer'
  )
}
</script>

<template>
  <div class="top-bar">

    <!-- LEFT -->
    <div class="top-bar-left">

      <!-- Facebook -->
      <a
        href="#"
        class="social-btn"
        aria-label="Facebook"
        target="_blank"
        rel="noopener noreferrer"
      >
        <svg viewBox="0 0 24 24">
          <path
            d="M13.5 22v-9h3l.45-3.5H13.5V7.25c0-1.01.28-1.7 1.73-1.7H17V2.42c-.31-.04-1.38-.13-2.62-.13-2.6 0-4.38 1.59-4.38 4.5V9.5H7v3.5h3v9h3.5Z"
          />
        </svg>
      </a>

      <!-- LinkedIn -->
      <a
        href="#"
        class="social-btn"
        aria-label="LinkedIn"
        target="_blank"
        rel="noopener noreferrer"
      >
        <svg viewBox="0 0 24 24">
          <path
            d="M6.5 8.5H3.25V21H6.5V8.5ZM4.88 3A1.88 1.88 0 1 0 4.88 6.75 1.88 1.88 0 0 0 4.88 3ZM21 13.83C21 10.06 18.99 8.3 16.31 8.3c-2.16 0-3.13 1.19-3.67 2.03V8.5H9.39V21h3.25v-6.19c0-1.63.31-3.21 2.34-3.21 2 0 2.03 1.87 2.03 3.32V21H21v-7.17Z"
          />
        </svg>
      </a>

      <!-- Instagram -->
      <a
        href="#"
        class="social-btn"
        aria-label="Instagram"
        target="_blank"
        rel="noopener noreferrer"
      >
        <svg viewBox="0 0 24 24">
          <path
            d="M7 2h10a5 5 0 0 1 5 5v10a5 5 0 0 1-5 5H7a5 5 0 0 1-5-5V7a5 5 0 0 1 5-5Zm0 2a3 3 0 0 0-3 3v10a3 3 0 0 0 3 3h10a3 3 0 0 0 3-3V7a3 3 0 0 0-3-3H7Zm5 3a5 5 0 1 1 0 10 5 5 0 0 1 0-10Zm0 2a3 3 0 1 0 0 6 3 3 0 0 0 0-6Zm5.5-3.25a1.25 1.25 0 1 1 0 2.5 1.25 1.25 0 0 1 0-2.5Z"
          />
        </svg>
      </a>

    </div>


    <!-- RIGHT -->
    <div class="top-bar-right">

      <a href="#blogs" class="top-link">
        Blogs
      </a>

      <a href="#contact" class="top-link">
        Contact Us
      </a>


      <!-- PHONE -->
      <a
        :href="`tel:${contact.phoneLink}`"
        class="top-link contact-link phone-link"
      >
        <svg viewBox="0 0 24 24">
          <path
            d="M6.62 10.79a15.46 15.46 0 0 0 6.59 6.59l2.2-2.2a1 1 0 0 1 1.02-.24c1.12.37 2.33.57 3.57.57a1 1 0 0 1 1 1V20a1 1 0 0 1-1 1C10.61 21 3 13.39 3 4a1 1 0 0 1 1-1h3.5a1 1 0 0 1 1 1c0 1.25.2 2.45.57 3.57a1 1 0 0 1-.25 1.02l-2.2 2.2Z"
          />
        </svg>

        {{ contact.phoneDisplay }}
      </a>


      <!-- EMAIL -->
      <a
        :href="`mailto:${contact.email}`"
        class="top-link contact-link email-link"
      >
        <svg viewBox="0 0 24 24">
          <path
            d="M20 4H4a2 2 0 0 0-2 2v12a2 2 0 0 0 2 2h16a2 2 0 0 0 2-2V6a2 2 0 0 0-2-2Zm0 4-8 5-8-5V6l8 5 8-5v2Z"
          />
        </svg>

        {{ contact.email }}
      </a>


      <!-- WHATSAPP -->
      <button
        class="whatsapp-btn"
        type="button"
        aria-label="WhatsApp"
        @click="openWhatsApp"
      >
        <svg viewBox="0 0 24 24">
          <path
            d="M12.04 2a9.84 9.84 0 0 0-8.4 14.95L2 22l5.2-1.62A9.95 9.95 0 1 0 12.04 2Zm0 17.8a7.84 7.84 0 0 1-4-1.1l-.29-.17-3.08.96 1-3-.19-.31A7.8 7.8 0 1 1 12.04 19.8Zm4.3-5.85c-.24-.12-1.4-.69-1.61-.77-.22-.08-.38-.12-.54.12-.16.24-.62.77-.76.93-.14.16-.28.18-.52.06-.24-.12-1-.37-1.9-1.18a7.13 7.13 0 0 1-1.32-1.64c-.14-.24-.01-.37.1-.49.11-.11.24-.28.36-.42.12-.14.16-.24.24-.4.08-.16.04-.3-.02-.42-.06-.12-.54-1.3-.74-1.78-.2-.47-.4-.4-.54-.41h-.46c-.16 0-.42.06-.64.3-.22.24-.84.82-.84 2s.86 2.32.98 2.48c.12.16 1.69 2.58 4.1 3.62.57.25 1.02.39 1.37.5.58.18 1.1.16 1.51.1.46-.07 1.4-.58 1.6-1.13.2-.56.2-1.04.14-1.14-.06-.1-.22-.16-.46-.28Z"
          />
        </svg>
      </button>


      <!-- LANGUAGE -->
      <div class="language-select">

        <!-- VISIBLE VALUE -->
        <span class="language-value">
          {{ selectedLanguage }}
        </span>

        <!-- REAL SELECT -->
        <select
          v-model="selectedLanguage"
          aria-label="Language"
        >
          <option value="English">
            English
          </option>

          <option value="සිංහල">
            සිංහල
          </option>

          <option value="தமிழ்">
            தமிழ்
          </option>
        </select>


        <!-- ARROW -->
        <svg
          class="select-arrow"
          viewBox="0 0 24 24"
          fill="none"
          stroke="currentColor"
          stroke-width="2"
        >
          <path d="m7 10 5 5 5-5" />
        </svg>

      </div>

    </div>

  </div>
</template>


<style scoped>

/* =========================================
   TOP BAR
========================================= */

.top-bar {
  position: relative;

  z-index: 1200;

  width: 100%;

  height: clamp(36px, 2.5vw, 42px);

  display: flex;
  align-items: center;
  justify-content: space-between;

  padding:
    0
    clamp(18px, 2.5vw, 48px);

  box-sizing: border-box;

  background: #f2f2f2;

  color: #111;

  font-family:
    'Oakes Grotesk',
    'Urbanist',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    sans-serif;
}


/* =========================================
   LEFT / RIGHT
========================================= */

.top-bar-left,
.top-bar-right {
  display: flex;
  align-items: center;
}

.top-bar-left {
  gap: clamp(6px, 0.6vw, 10px);
}

.top-bar-right {
  gap: clamp(12px, 1.3vw, 25px);
}


/* =========================================
   SOCIAL BUTTONS
========================================= */

.social-btn {
  width: clamp(28px, 2vw, 34px);
  height: clamp(28px, 2vw, 34px);

  display: flex;
  align-items: center;
  justify-content: center;

  flex-shrink: 0;

  border-radius: 50%;

  background: #ffffff;

  color: #111111;

  text-decoration: none;

  transition:
    background 0.25s ease,
    transform 0.25s ease;
}

.social-btn svg {
  width: 44%;
  height: 44%;

  fill: currentColor;
}

.social-btn:hover {
  background: #a3e635;

  transform: translateY(-2px);
}


/* =========================================
   TOP LINKS
========================================= */

.top-link {
  display: inline-flex;
  align-items: center;

  gap: 6px;

  color: #111111;

  font-size: clamp(10px, 0.78vw, 13px);

  font-weight: 600;

  white-space: nowrap;

  text-decoration: none;

  transition: color 0.2s ease;
}

.top-link:hover {
  color: #65a30d;
}

.contact-link svg {
  width: 14px;
  height: 14px;

  fill: currentColor;
}


/* =========================================
   WHATSAPP
========================================= */

.whatsapp-btn {
  width: clamp(28px, 2vw, 34px);
  height: clamp(28px, 2vw, 34px);

  display: flex;
  align-items: center;
  justify-content: center;

  flex-shrink: 0;

  padding: 0;

  border: none;

  border-radius: 50%;

  background: #a3e635;

  color: #0f172a;

  cursor: pointer;

  transition: transform 0.2s ease;
}

.whatsapp-btn:hover {
  transform: scale(1.07);
}

.whatsapp-btn svg {
  width: 54%;
  height: 54%;

  fill: currentColor;
}


/* =========================================
   LANGUAGE SELECT
========================================= */

.language-select {
  position: relative;

  width: clamp(105px, 9vw, 145px);

  height: clamp(30px, 2.2vw, 34px);

  display: flex;
  align-items: center;

  flex-shrink: 0;

  box-sizing: border-box;

  background: #ffffff;

  border: 1px solid #d6d6d6;

  border-radius: 7px;

  overflow: hidden;

  cursor: pointer;
}


/* =========================================
   VISIBLE LANGUAGE TEXT
========================================= */

.language-value {
  position: absolute;

  left: 12px;

  top: 50%;

  transform: translateY(-50%);

  z-index: 1;

  color: #111111;

  font-family: inherit;

  font-size: clamp(10px, 0.75vw, 12px);

  font-weight: 600;

  line-height: 1;

  pointer-events: none;

  white-space: nowrap;
}


/* =========================================
   REAL SELECT

   Invisible, but remains clickable.
========================================= */

.language-select select {
  position: absolute;

  inset: 0;

  z-index: 3;

  width: 100%;
  height: 100%;

  margin: 0;
  padding: 0;

  border: none;
  outline: none;

  opacity: 0;

  cursor: pointer;
}


/* =========================================
   SELECT ARROW
========================================= */

.select-arrow {
  position: absolute;

  top: 50%;
  right: 10px;

  z-index: 2;

  width: 13px;
  height: 13px;

  transform: translateY(-50%);

  color: #111111;

  pointer-events: none;
}


/* =========================================
   TABLET
========================================= */

@media (max-width: 1000px) {

  .email-link {
    display: none;
  }

}


/* =========================================
   SMALL TABLET
========================================= */

@media (max-width: 750px) {

  .top-link:not(.phone-link) {
    display: none;
  }

}


/* =========================================
   MOBILE
========================================= */

@media (max-width: 600px) {

  .top-bar {
    height: 40px;

    padding:
      0
      10px;
  }

  .phone-link {
    display: none;
  }

  .top-bar-right {
    gap: 7px;
  }

  .social-btn,
  .whatsapp-btn {
    width: 27px;
    height: 27px;
  }

  .language-select {
    width: 95px;

    height: 30px;
  }

  .language-value {
    left: 10px;

    font-size: 10px;
  }

  .select-arrow {
    right: 8px;
  }

}

</style>