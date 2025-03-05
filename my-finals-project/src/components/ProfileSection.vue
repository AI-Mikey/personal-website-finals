<template>
  <div>
    <section id="about" class="section">
      <h2 class="section-title">About Me</h2>
      <div class="about-content">
        <div class="about-image">
          <img src="https://github.com/AI-Mikey/personal-website-finals/raw/main/my-finals-project/img/2f310984-267c-4f21-b724-371132493d7f.jpg" alt="Michael and Girlfriend" />
        </div>
        <div class="about-text">
          <p>My name is <strong>Michael M. Orenze</strong>, and I'm 21 years old. I live in Bangkal, Makati. My favorite games right now are Warframe and Stardew Valley.</p>
        </div>
      </div>
    </section>

    <section id="education" class="section">
      <h2 class="section-title">Education & Achievements</h2>
      <div class="education-content">
        <div class="education-item">
          <div class="education-icon">
            <i class="fas fa-graduation-cap"></i>
          </div>
          <div class="education-details">
            <h3>Junior High School</h3>
            <p>JHS Graduate</p>
          </div>
        </div>
        <div class="education-item">
          <div class="education-icon">
            <i class="fas fa-award"></i>
          </div>
          <div class="education-details">
            <h3>Senior High School</h3>
            <p>SHS Graduate (Honor Student)</p>
          </div>
        </div>
        <div class="education-item">
          <div class="education-icon">
            <i class="fas fa-laptop-code"></i>
          </div>
          <div class="education-details">
            <h3>College</h3>
            <p>BSCS-SS (Bachelor of Science in Computer Science with specialization in Software Systems)</p>
          </div>
        </div>
        <div class="education-item">
          <div class="education-icon">
            <i class="fas fa-code"></i>
          </div>
          <div class="education-details">
            <h3>IT Experience</h3>
            <p>Python Project, Java Assignments, and a search engine project that plants a tree for every 50 searches.</p>
          </div>
        </div>
      </div>
    </section>

    <section id="hobbies" class="section">
      <h2 class="section-title">Hobbies & Interests</h2>
      <div class="hobbies-content">
        <div class="hobby-item">
          <div class="hobby-icon">
            <i class="fas fa-gamepad"></i>
          </div>
          <div class="hobby-details">
            <h3>Gaming</h3>
            <p>Playing games like Warframe and Stardew Valley</p>
          </div>
        </div>
        <div class="hobby-item">
          <div class="hobby-icon">
            <i class="fas fa-tv"></i>
          </div>
          <div class="hobby-details">
            <h3>Anime</h3>
            <p>Watching anime in my free time</p>
          </div>
        </div>
        <div class="hobby-item">
          <div class="hobby-icon">
            <i class="fas fa-users"></i>
          </div>
          <div class="hobby-details">
            <h3>Social</h3>
            <p>Spending time with my girlfriend, friends, and family</p>
          </div>
        </div>
      </div>
    </section>

    <section id="goal" class="section">
      <h2 class="section-title">Goal In Life</h2>
      <div class="goal-content">
        <div class="goal-icon">
          <i class="fas fa-star"></i>
        </div>
        <p>My goal in life is to become a successful programmer or game developer and have a wealthy, healthy, and happy family in the future with my girlfriend.</p>
      </div>
    </section>

    <section id="gallery" class="section">
      <h2 class="section-title">Picture Gallery</h2>
      <div class="gallery-content">
        <div v-for="(image, index) in images" :key="index" class="gallery-item" @click="openLightbox(index)">
          <img :src="image.url" :alt="image.name" />
          <div class="gallery-caption">{{ image.name }}</div>
        </div>
      </div>

      <!-- Lightbox -->
      <div class="lightbox" v-if="lightboxOpen" @click="closeLightbox">
        <div class="lightbox-content" @click.stop>
          <button class="lightbox-close" @click="closeLightbox">&times;</button>
          <button class="lightbox-prev" @click.stop="prevImage" v-if="images.length > 1">&lt;</button>
          <img :src="images[currentImageIndex].url" :alt="images[currentImageIndex].name" />
          <div class="lightbox-caption">{{ images[currentImageIndex].name }}</div>
          <button class="lightbox-next" @click.stop="nextImage" v-if="images.length > 1">&gt;</button>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const images = ref([
  {
    name: "Warframe Image 2023",
    url: "https://github.com/AI-Mikey/personal-website-finals/raw/main/my-finals-project/img/db7e90aa4e7b882bd39e50ffa30ca2db%20(1).jpg"
  },
  {
    name: "Instax Picture",
    url: "https://github.com/AI-Mikey/Images/raw/main/e3483601-12f7-4c74-b285-c32e9e002613.jpg"
  },
  {
    name: "UST Pic",
    url: "https://github.com/AI-Mikey/Images/raw/main/8a0826f4-143c-424a-89c4-4638e01b2699.jpg"
  },
  {
    name: "Photo Story",
    url: "https://github.com/AI-Mikey/Images/raw/main/6f8b4ec9-388d-48e9-918a-8ebbb077b4a6.jpg"
  },
  {
    name: "Manamn Pics",
    url: "https://github.com/AI-Mikey/Images/raw/main/2b43e76c-02dd-4625-bbb3-3b0ff00303a6.jpg"
  },
  {
    name: "Me and Girlfriend",
    url: "https://github.com/AI-Mikey/personal-website-finals/raw/main/my-finals-project/img/77c85b16-d8b6-4689-84bf-8dedb69cfd8f.jpg"
  },
  {
    name: "Bubu and Dudu",
    url: "https://github.com/AI-Mikey/webprogSS231-personal-website/blob/main/Image/image_2024-12-01_220542495.png?raw=true"
  },
  {
    name: "Together",
    url: "https://github.com/AI-Mikey/webprogSS231-personal-website/blob/main/Image/image_2024-12-01_220709048.png?raw=true"
  },
  {
    name: "Special Moment",
    url: "https://github.com/AI-Mikey/webprogSS231-personal-website/blob/main/Image/image_2024-12-01_221323296.png?raw=true"
  }
]);

const lightboxOpen = ref(false);
const currentImageIndex = ref(0);

const openLightbox = (index) => {
  currentImageIndex.value = index;
  lightboxOpen.value = true;
  document.body.style.overflow = 'hidden';
};

const closeLightbox = () => {
  lightboxOpen.value = false;
  document.body.style.overflow = '';
};

const nextImage = () => {
  currentImageIndex.value = (currentImageIndex.value + 1) % images.value.length;
};

const prevImage = () => {
  currentImageIndex.value = (currentImageIndex.value - 1 + images.value.length) % images.value.length;
};
</script>

<style scoped>
.about-content {
  display: flex;
  gap: 2rem;
  align-items: center;
}

.about-image {
  flex: 1;
  max-width: 300px;
}

.about-image img {
  width: 100%;
  border-radius: 10px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
}

.about-text {
  flex: 2;
}

.education-content, .hobbies-content {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 1.5rem;
}

.education-item, .hobby-item {
  display: flex;
  gap: 1rem;
  padding: 1rem;
  background-color: rgba(255, 255, 255, 0.8);
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.education-item:hover, .hobby-item:hover {
  transform: translateY(-5px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
}

.education-icon, .hobby-icon, .goal-icon {
  font-size: 2rem;
  color: var(--primary);
  display: flex;
  align-items: center;
  justify-content: center;
  width: 50px;
}

.goal-content {
  display: flex;
  align-items: center;
  gap: 1.5rem;
  padding: 1.5rem;
  background-color: rgba(255, 255, 255, 0.8);
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.gallery-content {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  gap: 1rem;
}

.gallery-item {
  position: relative;
  overflow: hidden;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  cursor: pointer;
  transition: transform 0.3s ease;
}

.gallery-item:hover {
  transform: scale(1.03);
}

.gallery-item img {
  width: 100%;
  height: 200px;
  object-fit: cover;
  display: block;
}

.gallery-caption {
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: rgba(0, 0, 0, 0.7);
  color: white;
  padding: 0.5rem;
  font-size: 0.9rem;
  transform: translateY(100%);
  transition: transform 0.3s ease;
}

.gallery-item:hover .gallery-caption {
  transform: translateY(0);
}

/* Lightbox styles */
.lightbox {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.9);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.lightbox-content {
  position: relative;
  max-width: 90%;
  max-height: 90%;
}

.lightbox-content img {
  max-width: 100%;
  max-height: 80vh;
  display: block;
  margin: 0 auto;
}

.lightbox-caption {
  color: white;
  text-align: center;
  padding: 1rem;
}

.lightbox-close, .lightbox-prev, .lightbox-next {
  background: none;
  border: none;
  color: white;
  font-size: 2rem;
  cursor: pointer;
  position: absolute;
}

.lightbox-close {
  top: 10px;
  right: 10px;
}

.lightbox-prev {
  left: -50px;
  top: 50%;
  transform: translateY(-50%);
}

.lightbox-next {
  right: -50px;
  top: 50%;
  transform: translateY(-50%);
}

@media (max-width: 768px) {
  .about-content {
    flex-direction: column;
  }
  
  .about-image {
    max-width: 100%;
  }
  
  .lightbox-prev {
    left: 10px;
  }
  
  .lightbox-next {
    right: 10px;
  }
}
</style>