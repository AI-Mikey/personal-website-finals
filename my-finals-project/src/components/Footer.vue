<template>
  <footer class="footer">
    <div class="footer-container">
      <div class="footer-section">
        <h3>Contact Me</h3>
        <p><i class="fas fa-phone"></i> +63 995 390 6266</p>
        <p><i class="fas fa-envelope"></i> <a href="mailto:mmorenze@student.apc.edu.ph">mmorenze@student.apc.edu.ph</a></p>
      </div>
      
      <div class="footer-section">
        <h3>Connect With Me</h3>
        <div class="social-links">
          <a href="https://www.linkedin.com/in/michael-orenze-59753a289/" title="LinkedIn" target="_blank">
            <i class="fab fa-linkedin"></i>
          </a>
          <a href="https://www.instagram.com/mikeykiddooooo/" title="Instagram" target="_blank">
            <i class="fab fa-instagram"></i>
          </a>
          <a href="https://www.facebook.com/michael.orenze.5" title="Facebook" target="_blank">
            <i class="fab fa-facebook"></i>
          </a>
          <a href="https://github.com/AI-Mikey" title="GitHub" target="_blank">
            <i class="fab fa-github"></i>
          </a>
        </div>
      </div>
    </div>
    <div class="footer-bottom">
      <p>&copy; {{ new Date().getFullYear() }} Michael M. Orenze. Operator, Tenno.</p>
    </div>
  </footer>
</template>

<script setup>
// No additional script needed
</script>

<style scoped>
.footer {
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  color: white;
  padding: 2rem 0 1rem;
  margin-top: 2rem;
}

.footer-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 1rem;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  gap: 2rem;
}

.footer-section {
  flex: 1;
  min-width: 250px;
}

.footer-section h3 {
  margin-bottom: 1rem;
  font-size: 1.2rem;
  position: relative;
  display: inline-block;
}

.footer-section h3::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -5px;
  width: 50px;
  height: 2px;
  background-color: white;
}

.footer-section p {
  margin-bottom: 0.5rem;
}

.footer-section a {
  color: white;
  text-decoration: none;
  transition: opacity 0.3s ease;
}

.footer-section a:hover {
  opacity: 0.8;
}

.social-links {
  display: flex;
  gap: 1rem;
  margin-top: 0.5rem;
}

.social-links a {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  background-color: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  transition: background-color 0.3s ease;
}

.social-links a:hover {
  background-color: rgba(255, 255, 255, 0.2);
}

.social-links i {
  font-size: 1.2rem;
}

.footer-bottom {
  max-width: 1200px;
  margin: 0 auto;
  padding: 1rem;
  text-align: center;
  border-top: 1px solid rgba(255, 255, 255, 0.1);
  margin-top: 2rem;
}

.footer-bottom p {
  margin: 0;
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .footer-container {
    flex-direction: column;
    gap: 1.5rem;
  }
}
</style>