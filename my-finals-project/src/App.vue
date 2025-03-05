<template>
  <div class="app">
    <Header />
    <main>
      <ProfileSection />
      <GuestbookSection />
    </main>
    <Footer />
  </div>
</template>

<script setup>
import Header from './components/Header.vue';
import ProfileSection from './components/ProfileSection.vue';
import GuestbookSection from './components/GuestbookSection.vue';
import Footer from './components/Footer.vue';
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap');

:root {
  --primary: #3a86ff;
  --secondary: #8338ec;
  --accent: #ff006e;
  --background: #f8f9fa;
  --text: #212529;
  --light-text: #6c757d;
  --card-bg: #ffffff;
  --border: #dee2e6;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: 'Poppins', sans-serif;
  background-color: var(--background);
  color: var(--text);
  line-height: 1.6;
}

.app {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

main {
  flex: 1;
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 1rem;
  width: 100%;
}

h1, h2, h3, h4, h5, h6 {
  margin-bottom: 1rem;
  font-weight: 600;
}

a {
  color: var(--primary);
  text-decoration: none;
  transition: color 0.3s ease;
}

a:hover {
  color: var(--secondary);
}

.section {
  margin-bottom: 3rem;
  padding: 2rem;
  background-color: var(--card-bg);
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.section-title {
  font-size: 1.8rem;
  color: var(--primary);
  margin-bottom: 1.5rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid var(--secondary);
  display: inline-block;
}

.btn {
  display: inline-block;
  padding: 0.5rem 1.5rem;
  background-color: var(--primary);
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s ease;
}

.btn:hover {
  background-color: var(--secondary);
}

.btn:disabled {
  background-color: var(--light-text);
  cursor: not-allowed;
}

@media (max-width: 768px) {
  .section {
    padding: 1.5rem;
  }
}
</style>