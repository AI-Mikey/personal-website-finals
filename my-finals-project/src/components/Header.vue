<template>
  <header class="header">
    <div class="header-container">
      <h1 class="logo">Michael M. Orenze</h1>
      <nav class="nav">
        <ul class="nav-list">
          <li><a href="#about" @click="scrollToSection('about')">About Me</a></li>
          <li><a href="#education" @click="scrollToSection('education')">Education</a></li>
          <li><a href="#hobbies" @click="scrollToSection('hobbies')">Hobbies</a></li>
          <li><a href="#goal" @click="scrollToSection('goal')">Goals</a></li>
          <li><a href="#gallery" @click="scrollToSection('gallery')">Gallery</a></li>
          <li><a href="#guestbook" @click="scrollToSection('guestbook')">Guestbook</a></li>
        </ul>
      </nav>
      <button class="mobile-menu-btn" @click="toggleMobileMenu">
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </button>
    </div>
    <div class="mobile-nav" :class="{ 'active': mobileMenuOpen }">
      <ul class="mobile-nav-list">
        <li><a href="#about" @click="handleMobileNavClick('about')">About Me</a></li>
        <li><a href="#education" @click="handleMobileNavClick('education')">Education</a></li>
        <li><a href="#hobbies" @click="handleMobileNavClick('hobbies')">Hobbies</a></li>
        <li><a href="#goal" @click="handleMobileNavClick('goal')">Goals</a></li>
        <li><a href="#gallery" @click="handleMobileNavClick('gallery')">Gallery</a></li>
        <li><a href="#guestbook" @click="handleMobileNavClick('guestbook')">Guestbook</a></li>
      </ul>
    </div>
  </header>
</template>

<script setup>
import { ref } from 'vue';

const mobileMenuOpen = ref(false);

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value;
};

const scrollToSection = (sectionId) => {
  const element = document.getElementById(sectionId);
  if (element) {
    element.scrollIntoView({ behavior: 'smooth' });
  }
};

const handleMobileNavClick = (sectionId) => {
  scrollToSection(sectionId);
  mobileMenuOpen.value = false;
};
</script>

<style scoped>
.section {
  background: url('https://github.com/AI-Mikey/personal-website-finals/raw/main/my-finals-project/img/wallpapersden.com_new-warframe-2023_1920x960%20(3).jpg') no-repeat center center;
  background-size: cover;
  padding: 50px 20px; /* Adjust padding as needed */
  color: white; /* Change text color for contrast */
}

.header {
  background: url('https://github.com/AI-Mikey/personal-website-finals/raw/main/my-finals-project/img/pngtree-japanese-style-wave-banner-background-vector-material-picture-image_1191544.jpg') no-repeat center center;
  background-size: cover;
  padding: 20px 20px; /* Adjust padding as needed */
  color: white; /* Change text color for contrast */
}

.header-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-size: 1.5rem;
  font-weight: 700;
  margin: 0;
}

.nav-list {
  display: flex;
  list-style: none;
  gap: 1.5rem;
}

.nav-list a {
  color: black;
  text-decoration: none;
  font-weight: 500;
  transition: opacity 0.3s ease;
}

.nav-list a:hover {
  opacity: 0.8;
}

.mobile-menu-btn {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0.5rem;
}

.bar {
  display: block;
  width: 25px;
  height: 3px;
  margin: 5px auto;
  background-color: white;
  transition: all 0.3s ease;
}

.mobile-nav {
  display: none;
  background-color: var(--primary);
  padding: 1rem;
  transform: translateY(-100%);
  transition: transform 0.3s ease;
}

.mobile-nav.active {
  transform: translateY(0);
}

.mobile-nav-list {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.mobile-nav-list a {
  color: white;
  text-decoration: none;
  font-weight: 500;
  display: block;
  padding: 0.5rem 0;
}

@media (max-width: 768px) {
  .nav {
    display: none;
  }

  .mobile-menu-btn {
    display: block;
  }

  .mobile-nav {
    display: block;
  }
}
</style>