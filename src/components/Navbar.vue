<script setup>
import { ref } from 'vue'

const isMenuOpen = ref(false)

const navLinks = ref([
  { id: 'home', label: 'HOME', href: '#'},
  { id: 'acca', label: 'ACCA', href: '#'},
  { id: 'cfa', label: 'CFA', href: '#' },
  { id: 'courses', label: 'COURSES', href: '#' },
  { id: 'contact', label: 'CONTACT', href: '#' }
])

// Which link is highlighted as the current page (like "Our Team" in the reference)
const activeId = ref('home')

const ctaLink = {
  label: 'Contact Us',
  href: 'https://alphabusiness.org.lk/login/index.php'
}

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}
</script>

<template>
  <nav class="navbar">
    <a href="https://www.alphabusiness.lk/" class="logo">Alpha Business School</a>

    <!-- DESKTOP NAV LINKS -->
    <ul class="nav-links">
      <li v-for="link in navLinks" :key="link.id">
        <a
          :href="link.href"
          :class="{ active: link.id === activeId }"
          @click="activeId = link.id"
        >
          <span v-if="link.flag" class="nav-flag" aria-hidden="true">{{ link.flag }}</span>
          {{ link.label }}
        </a>
      </li>
    </ul>

    <a :href="ctaLink.href" class="cta-btn">{{ ctaLink.label }}</a>

    <!-- MOBILE HAMBURGER -->
    <button
      class="menu"
      :class="{ open: isMenuOpen }"
      @click="toggleMenu"
      :aria-expanded="isMenuOpen"
      aria-label="Toggle navigation menu"
    >
      <span></span>
      <span></span>
      <span></span>
    </button>

    <!-- MOBILE DROPDOWN -->
    <ul class="mobile-menu" v-if="isMenuOpen">
      <li v-for="link in navLinks" :key="link.id">
        <a
          :href="link.href"
          :class="{ active: link.id === activeId }"
          @click="activeId = link.id; closeMenu()"
        >
          <span v-if="link.flag" class="nav-flag" aria-hidden="true">{{ link.flag }}</span>
          {{ link.label }}
        </a>
      </li>
      <li>
        <a :href="ctaLink.href" class="cta-btn mobile" @click="closeMenu">{{ ctaLink.label }}</a>
      </li>
    </ul>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  width: 100%;
  height: 76px;
  background: #ffffff;

  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 4vw;
  font-family: 'Oakes Grotesk', 'Urbanist', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

/* LOGO / WORDMARK */
.logo {
  font-size: 16px;
  font-weight: 650;
  letter-spacing: 1px;
  color: #0f172a;
  text-decoration: none;
  font-family: inherit;
  white-space: nowrap;
}

/* DESKTOP NAV LINKS */
.nav-links {
  display: flex;
  align-items: center;
  gap: 36px;
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-links a {
  display: inline-flex;
  align-items: center;
  gap: 6px;
  font-size: 14px;
  font-weight: 600;
  color: #0f172a;
  text-decoration: none;
  font-family: inherit;
  transition: color 0.2s ease;
  white-space: nowrap;
}

.nav-links a:hover {
  color: #048531;
}

.nav-links a.active {
  color: #048531;
  font-weight: 600;
}

.nav-flag {
  font-size: 14px;
  line-height: 1;
}

/* CTA PILL BUTTON */
.cta-btn {
  padding: 8px 28px;
  border-radius: 999px;
  background: #0f172a;
  color: #ffffff;
  font-size: 15px;
  font-weight: 600;
  text-decoration: none;
  font-family: inherit;
  white-space: nowrap;
  transition: opacity 0.2s ease, transform 0.2s ease;
}

.cta-btn:hover {
  opacity: 0.85;
  transform: translateY(-1px);
}

/* MOBILE HAMBURGER */
.menu {
  display: none;
  flex-direction: column;
  justify-content: center;
  gap: 5px;
  width: 24px;
  height: 24px;
  cursor: pointer;
  background: transparent;
  border: none;
  padding: 0;
}

.menu span {
  width: 100%;
  height: 2px;
  background: #0f172a;
  border-radius: 2px;
  transition: transform 0.2s ease, opacity 0.2s ease;
}

.menu.open span:nth-child(1) {
  transform: translateY(7px) rotate(45deg);
}

.menu.open span:nth-child(2) {
  opacity: 0;
}

.menu.open span:nth-child(3) {
  transform: translateY(-7px) rotate(-45deg);
}

/* MOBILE DROPDOWN */
.mobile-menu {
  display: none;
}

/* RESPONSIVE BREAKPOINTS (matching site convention: 900px / 640px) */
@media (max-width: 900px) {
  .nav-links,
  .cta-btn:not(.mobile) {
    display: none;
  }

  .menu {
    display: flex;
  }

  .mobile-menu {
    display: flex;
    flex-direction: column;
    position: absolute;
    top: 76px;
    left: 0;
    right: 0;
    background: #ffffff;
    padding: 16px 4vw 24px;
    gap: 4px;
    list-style: none;
    margin: 0;
    border-bottom: 1px solid #e2e8f0;
    box-shadow: 0 8px 16px rgba(15, 23, 42, 0.06);
  }

  .mobile-menu a {
    display: flex;
    align-items: center;
    gap: 8px;
    padding: 12px 4px;
    font-size: 15px;
    font-weight: 600;
    color: #0f172a;
    text-decoration: none;
    font-family: inherit;
    border-bottom: 1px solid #f1f5f9;
  }

  .mobile-menu a.active {
    color: #d97706;
  }

  .cta-btn.mobile {
    display: inline-flex;
    justify-content: center;
    margin-top: 8px;
    border-bottom: none;
  }
}

@media (max-width: 640px) {
  .logo {
    font-size: 18px;
  }
}
</style>
