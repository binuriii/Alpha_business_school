```vue
<script setup>
import { ref } from 'vue'

const currentYear = new Date().getFullYear()

const email = ref('')

const footerColumns = ref([
  {
    id: 'programs',
    title: 'Programs',
    links: [
      { label: 'MBA', href: '#' },
      { label: 'Data Science', href: '#' },
      { label: 'Business Analytics', href: '#' },
      { label: 'Executive Education', href: '#' },
      { label: 'Short Courses', href: '#' }
    ]
  },
  {
    id: 'campus-life',
    title: 'Campus Life',
    links: [
      { label: 'Student Clubs', href: '#' },
      { label: 'Events & Festivals', href: '#' },
      { label: 'Sports & Athletics', href: '#' },
      { label: 'Housing', href: '#' },
      { label: 'Career Services', href: '#' }
    ]
  },
  {
    id: 'admissions',
    title: 'Admissions',
    links: [
      { label: 'How to Apply', href: '#' },
      { label: 'Tuition & Fees', href: '#' },
      { label: 'Scholarships', href: '#' },
      { label: 'International Students', href: '#' },
      { label: 'FAQs', href: '#' }
    ]
  },
  {
    id: 'about',
    title: 'About Alpha',
    links: [
      { label: 'Our Story', href: '#' },
      { label: 'Faculty', href: '#' },
      { label: 'News & Press', href: '#' },
      { label: 'Careers', href: '#' },
      { label: 'Contact Us', href: '#' }
    ]
  }
])

const socialLinks = ref([
  { id: 'linkedin', label: 'LinkedIn', href: '#' },
  { id: 'instagram', label: 'Instagram', href: '#' },
  { id: 'youtube', label: 'YouTube', href: '#' },
  { id: 'x', label: 'X (Twitter)', href: '#' }
])

const legalLinks = ref([
  { label: 'Privacy Policy', href: '#' },
  { label: 'Terms of Service', href: '#' },
  { label: 'Sitemap', href: '#' },
  { label: 'Accessibility', href: '#' }
])

const handleSubscribe = () => {
  if (email.value) {
    alert(`Subscribed with: ${email.value}`)
    email.value = ''
  }
}
</script>

<template>
  <footer
    class="seo-footer"
    itemscope
    itemtype="https://schema.org/EducationalOrganization"
  >
    <div class="footer-inner">

      <!-- TOP -->
      <div class="footer-top">

        <!-- BRAND -->
        <div class="footer-brand">
          <h2 itemprop="name">Alpha Business School</h2>

          <p itemprop="description">
            Alpha Business School equips students with in-demand business,
            data and leadership skills through world-class faculty,
            hands-on programs and a vibrant, inclusive campus community.
          </p>

          <ul
            class="social-list"
            aria-label="Alpha Business School on social media"
          >
            <li
              v-for="social in socialLinks"
              :key="social.id"
            >
              <a
                :href="social.href"
                class="social-link"
                :aria-label="social.label"
              >
                {{ social.label }}
              </a>
            </li>
          </ul>
        </div>

        <!-- LINK COLUMNS -->
        <nav
          v-for="column in footerColumns"
          :key="column.id"
          class="footer-column"
          :aria-label="column.title"
        >
          <h3>{{ column.title }}</h3>

          <ul>
            <li
              v-for="link in column.links"
              :key="link.label"
            >
              <a :href="link.href">
                {{ link.label }}
              </a>
            </li>
          </ul>
        </nav>

      </div>

      <!-- NEWSLETTER -->
      <div class="footer-subscribe">

        <div class="subscribe-text">
          <h3>Subscribe to our newsletter</h3>

          <p>
            Get the latest news, updates, and event alerts
            delivered directly to your inbox.
          </p>
        </div>

        <form
          @submit.prevent="handleSubscribe"
          class="subscribe-form"
        >
          <input
            v-model="email"
            type="email"
            placeholder="Type your email address"
            required
            aria-label="Email Address"
          />

          <button
            type="submit"
            class="subscribe-btn"
          >
            Subscribe

            <svg
              class="arrow-icon"
              viewBox="0 0 24 24"
              fill="none"
              stroke="currentColor"
              stroke-width="2.5"
            >
              <path d="M7 17L17 7M17 7H7M17 7V17" />
            </svg>
          </button>
        </form>

      </div>

      <!-- BOTTOM -->
      <div class="footer-bottom">

        <p class="copyright">
          &copy; {{ currentYear }}
          Alpha Business School. All rights reserved.
        </p>

        <ul class="legal-list">
          <li
            v-for="(link, index) in legalLinks"
            :key="link.label"
          >
            <a :href="link.href">
              {{ link.label }}
            </a>

            <span
              v-if="index < legalLinks.length - 1"
              class="divider"
              aria-hidden="true"
            >
              /
            </span>
          </li>
        </ul>

      </div>

    </div>
  </footer>
</template>

<style scoped>

.seo-footer {
  width: 100%;
  max-width: none;
  background: #f8fafc;
  box-sizing: border-box;

  padding:
    clamp(45px, 5vw, 85px)
    clamp(24px, 5vw, 90px)
    clamp(25px, 3vw, 45px);

  font-family:
    'Oakes Grotesk',
    'Urbanist',
    -apple-system,
    BlinkMacSystemFont,
    sans-serif;
}

.footer-inner {
  width: 100%;
  max-width: none;
  margin: 0;
}

.footer-top {
  width: 100%;

  display: grid;

  grid-template-columns:
    minmax(280px, 1.7fr)
    repeat(4, minmax(150px, 1fr));

  gap: clamp(35px, 5vw, 100px);

  padding-bottom: clamp(35px, 4vw, 60px);

  border-bottom: 1px solid #e2e8f0;
}

.footer-brand {
  max-width: 390px;
}

.footer-brand h2 {
  margin: 0 0 18px;

  font-size: clamp(21px, 1.5vw, 27px);
  font-weight: 600;
  line-height: 1.2;

  color: #0f172a;
}

.footer-brand p {
  margin: 0 0 24px;

  max-width: 380px;

  font-size: clamp(12px, 0.8vw, 14px);
  line-height: 1.65;

  color: #64748b;
}

.social-list {
  list-style: none;

  margin: 0;
  padding: 0;

  display: flex;
  flex-wrap: wrap;

  gap: 10px 20px;
}

.social-link {
  font-size: clamp(11px, 0.75vw, 13px);
  font-weight: 700;

  color: #0f172a;
  text-decoration: none;

  transition: opacity 0.2s ease;
}

.social-link:hover {
  opacity: 0.6;
}

.footer-column {
  min-width: 0;
}

.footer-column h3 {
  margin: 0 0 18px;

  font-size: clamp(13px, 0.8vw, 15px);
  font-weight: 600;

  color: #0f172a;
}

.footer-column ul {
  list-style: none;

  margin: 0;
  padding: 0;

  display: flex;
  flex-direction: column;

  gap: 12px;
}

.footer-column a {
  display: inline-block;

  font-size: clamp(11px, 0.75vw, 13px);
  line-height: 1.5;

  color: #64748b;
  text-decoration: none;

  transition:
    color 0.2s ease,
    transform 0.2s ease;
}

.footer-column a:hover {
  color: #0f172a;
  transform: translateX(2px);
}

.footer-subscribe {
  width: 100%;

  display: flex;
  align-items: center;
  justify-content: space-between;

  gap: 40px;

  padding:
    clamp(30px, 3.5vw, 50px)
    0;

  border-bottom: 1px solid #e2e8f0;
}

.subscribe-text {
  min-width: 0;
}

.subscribe-text h3 {
  margin: 0 0 7px;

  font-size: clamp(17px, 1.2vw, 20px);
  font-weight: 600;

  color: #0f172a;
}

.subscribe-text p {
  margin: 0;

  font-size: clamp(11px, 0.75vw, 13px);
  line-height: 1.5;

  color: #64748b;
}

.subscribe-form {
  flex: 0 1 480px;

  min-width: 320px;

  display: flex;
  align-items: center;

  gap: 8px;

  padding: 5px 5px 5px 18px;

  background: #ffffff;

  border: 1px solid #e2e8f0;

  border-radius: 40px;

  box-sizing: border-box;

  transition:
    border-color 0.2s ease,
    box-shadow 0.2s ease;
}

.subscribe-form:focus-within {
  border-color: #0f172a;

  box-shadow:
    0 0 0 3px rgba(15, 23, 42, 0.04);
}

.subscribe-form input {
  min-width: 0;
  width: 100%;

  flex: 1;

  border: none;
  outline: none;

  background: transparent;

  font-family: inherit;

  font-size: 13px;

  color: #0f172a;
}

.subscribe-form input::placeholder {
  color: #94a3b8;
}

.subscribe-btn {
  flex-shrink: 0;

  display: flex;
  align-items: center;
  justify-content: center;

  gap: 7px;

  padding: 11px 19px;

  border: none;
  border-radius: 25px;

  background: #0f172a;
  color: #ffffff;

  font-family: inherit;

  font-size: 12px;
  font-weight: 700;

  cursor: pointer;

  transition:
    background-color 0.2s ease,
    transform 0.2s ease;
}

.subscribe-btn:hover {
  background: #1e293b;
  transform: translateY(-1px);
}

.arrow-icon {
  width: 12px;
  height: 12px;
}

.footer-bottom {
  width: 100%;

  display: flex;
  align-items: center;
  justify-content: space-between;

  gap: 20px;

  padding-top: 25px;
}

.copyright {
  margin: 0;

  font-size: 11px;

  color: #64748b;
}

.legal-list {
  list-style: none;

  margin: 0;
  padding: 0;

  display: flex;
  align-items: center;
  flex-wrap: wrap;

  gap: 8px;
}

.legal-list li {
  display: flex;
  align-items: center;

  gap: 8px;
}

.legal-list a {
  font-size: 11px;

  color: #64748b;

  text-decoration: none;

  transition: color 0.2s ease;
}

.legal-list a:hover {
  color: #0f172a;
}

.divider {
  color: #cbd5e1;
  font-size: 11px;
}

@media (min-width: 1600px) {
  .seo-footer {
    padding-left: 6vw;
    padding-right: 6vw;
  }

  .footer-top {
    grid-template-columns:
      minmax(340px, 1.8fr)
      repeat(4, minmax(180px, 1fr));

    gap: 6vw;
  }

  .footer-brand {
    max-width: 430px;
  }
}

@media (max-width: 1100px) {
  .footer-top {
    grid-template-columns:
      1.5fr
      repeat(2, 1fr)
      repeat(2, 1fr);

    gap: 35px;
  }

  .footer-subscribe {
    align-items: flex-start;
  }

  .subscribe-form {
    flex-basis: 400px;
  }
}

@media (max-width: 800px) {
  .seo-footer {
    padding:
      45px
      30px
      25px;
  }

  .footer-top {
    grid-template-columns: repeat(2, 1fr);
    gap: 40px 30px;
  }

  .footer-brand {
    grid-column: 1 / -1;
    max-width: 600px;
  }

  .footer-subscribe {
    flex-direction: column;
    align-items: stretch;

    gap: 25px;
  }

  .subscribe-form {
    width: 100%;
    max-width: none;
    flex-basis: auto;
  }
}

@media (max-width: 560px) {
  .seo-footer {
    padding:
      40px
      20px
      22px;
  }

  .footer-top {
    grid-template-columns: 1fr;
    gap: 32px;
  }

  .footer-brand {
    grid-column: auto;
  }

  .footer-subscribe {
    gap: 20px;
  }

  .subscribe-form {
    min-width: 0;
    width: 100%;
  }

  .subscribe-btn {
    padding: 10px 15px;
  }

  .footer-bottom {
    flex-direction: column;
    align-items: flex-start;
  }

  .legal-list {
    gap: 7px;
  }
}
</style>
```
