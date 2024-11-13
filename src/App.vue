<template>
  <div id="app">
    <!-- Header -->
    <header class="header">
      <div class="nav container">
        <div class="logo">
          <!-- Logo Image -->
          <!-- <img src="@\assets\nmf-7.png" alt="NMFF Logo" class="logo-image" /> -->
          <img src="@\assets\logoNMF.png" alt="NMFF Logo" class="logo-image" />
          <!-- Logo Text -->
          <span class="logo-text">NMF</span>
        </div>

        <div class="nav-links" :class="{ 'nav-active': menuActive }">
          <a href="#home" @click="scrollToSection('home')">Home</a>
          <a href="#schedule" @click="scrollToSection('schedule')">Event Schedule</a>
          <a href="#participation" @click="scrollToSection('participation')">Participate</a>
          <a href="#registration" @click="scrollToSection('registration')">Ambassador Registration</a>
          <a href="#contact" @click="scrollToSection('contact')">Contact Us</a>
        </div>
        <div class="menu-toggle" :class="{ 'active': menuActive }" @click="toggleMenu">
          <span></span>
          <span></span>
          <span></span>
        </div>
      </div>
    </header>

    <!-- Hero Section -->
    <section class="hero" id="home">
      <div class="overlay">
        <img src="@\assets\nmf-7(1).png" alt="NMFF Logo" class="logo-image" />
        <h1 id="hero-heading">دل کی دھڑکنوں کو <span class="orange">موسیقی</span> کے ساتھ ملائیں</h1>
        <h2>National Music Festival 2.0</h2>
        <p>NUST, H-12, Islamabad | 28-29 November 2024</p>
        <!-- <a href="https://docs.google.com/forms/d/e/1FAIpQLSewJKQbnhNKDRAmlVwEbYqJF4P2pIZWu5h9x2VLkY6AA9A-yw/viewform?usp=sf_link">
          <button class="register-btn">Buy Tickets</button>
        </a> -->
        <div class="countdown">
          <div>
            <span>{{ days }}</span>
            <p>Days</p>
          </div>
          <div >
            <span>{{ hours }}</span>
            <p>Hours</p>
          </div>
          <div class="none-sm">
            <span>{{ minutes }}</span>
            <p>Minutes</p>
          </div>
          <div class="none-sm">
            <span>{{ seconds }}</span>
            <p>Seconds</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Why Join Section -->
    <section class="why-join" id="why-join">
      <h2>Why You Should Join</h2>
      <div class="features container">
        <div class="feature-box">
          <img src="https://t4.ftcdn.net/jpg/06/83/48/05/360_F_683480571_leNz6IF9RQ3GtmNO9dl8RuLAreTa4CZ5.jpg" alt="Live Performances">
          <h3>Live Performances</h3>
          <p>Enjoy electrifying performances from upcoming artists and bands.</p>
        </div>
        <div class="feature-box">
          <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR4TVsSSg_dMzV4ZrJrpBlPgl_otZim5sIv_tc7eBdU60vMVysLS6kO7F2jWrzlnNnxrhs&usqp=CAU" alt="Music Workshops">
          <h3>Competitions</h3>
          <p>Test your talent in front of renowned artists and make your mark in the field.</p>
        </div>
        <div class="feature-box">
          <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcScTBBcH1izkY2TuQZft1_cQrTvsLY4m1xNenuMU3f7t6PqjGVPY3mNsW9ri8NVy0xzs-U&usqp=CAU" alt="Networking">
          <h3>Networking</h3>
          <p>Connect with fellow music enthusiasts and expand your network.</p>
        </div>
        <div class="feature-box">
          <img src="https://melodystudio.net/wp-content/uploads/2023/07/MelodyStudio-Blog-What-You-Must-Know-Before-Joining-a-Pro-Jam-Session.jpg" alt="Food & Fun">
          <h3>Jamming Sessions</h3>
          <p>
            Engage in the most iconic gatherings with fellow musicians in NUST's majestic atmosphere.
          </p>
        </div>
      </div>
    </section>

    <!-- Gallery Section -->
    <section class="gallery" id="gallery">
      <h2 id="hero-heading">موسیقی کے <span class="orange">رنگ</span></h2>
      <h2 style="text-align: center; margin-top: 2rem; font-size: 2rem">Highlights from  <span class="orange">NMF 1.0</span></h2>
      <div class="carousel">
        <div class="carousel-slide" :style="{ backgroundImage: 'url(' + images[currentImage].url + ')' }">
          <div class="carousel-text">
            <p>{{ images[currentImage].text }}</p>
          </div>
        </div>
        <div class="carousel-controls">
          <span class="prev" @click="prevImage">&#10094;</span>
          <span class="next" @click="nextImage">&#10095;</span>
        </div>
        <div class="carousel-indicators">
          <span v-for="(image, index) in images" :key="index" :class="{ active: currentImage === index }" @click="goToImage(index)"></span>
        </div>
      </div>
    </section>

    <!-- Participation Section -->
    <section class="participation" id="participation">
      <h2 id="hero-heading">
        <span class="orange">موسیقی کے میلے</span> کا حصہ بنیں
      </h2>
      <p>Are you an artist, musician, or performer looking to showcase your talent?</p>
      <p>Join us at the <b>National Music Festival 2.0!</b></p>
      <a href="https://docs.google.com/forms/d/e/1FAIpQLSfiUXOCB_fd06rYBHMrMCsT6-BfY7Mje5BNVH8R_CGdlunvWA/viewform?usp=sf_link" target="_blank" class="participate-btn">Participate Now</a>
      <p style="margin-top: 12px;font-size: 14px">Students from any institution in Pakistan can register</p>
    </section>

    <!-- Schedule Section -->
    <section class="schedule" id="schedule">
      <h2>Event Schedule</h2>
      <div class="days container">
        <div class="day">
          <h3>Day 1 (November 28th, 2024)</h3>
          <ul>
            <li><strong>Song Association (1000 – 1300 hrs.)</strong> - Teams will compete in a fun, word-based song game to engage the audience.</li>
            <li><strong>Eastern Singing Competition (1300 – 1700 hrs.)</strong> - A showcase of vocal talent in Eastern music, judged by renowned professionals.</li>
            <li><strong>Western Singing Competition (1700 – 2100 hrs.)</strong> - Participants will perform Western songs, with expert judges selecting winners.</li>
          </ul>
        </div>
        <div class="day">
          <h3>Day 2 (November 29th, 2024)</h3>
          <ul>
            <li><strong>Instrumental Competition (1000 – 1200 hrs.)</strong> - A platform for musicians to perform solo pieces on their favourite songs.</li>
            <li><strong>Battle of the Bands  (1500 – 2100 hrs.)</strong> - The biggest event of the festival featuring 15 university bands, culminating in a final round with a grand prize for the winner</li>
          </ul>
        </div>
      </div>
    </section>

    <!-- Registration Section -->
    <section class="registration" id="registration">
      <div class="overlay">
        <h2>Call for Campus Ambassadors</h2>
        <h3 id="hero-heading">
          <span class="orange">موسیقی کے میلے</span> کا حصہ بنیں
        </h3>
        <p>
          Bring participants from your campus and get exciting incentives at the greatest Music Festival to be witnessed at NUST.
        </p>
        <a href="https://docs.google.com/forms/d/e/1FAIpQLSdIXb9a_TrIh9-P-4ypo4dOZwtZ4RMfgVPR0mmzluAIgY36jA/viewform?usp=sf_link" target="_blank">
          <button class="register-btn">Ambassador Registration</button>
        </a>
        <!-- <p style="margin-top: 12px;font-size: 14px">
          Only NUSTians are allowed!
        </p> -->
      </div>
    </section>

    <!-- Footer -->
    <footer>
      <div class="footer-container container">
        <div class="footer-about">
          <h2>National Music Festival</h2>
          <p>Bringing together music lovers from all over the country.</p>
          <ul class="social-icons">
            <li><a href="https://www.instagram.com/nationalmusicfestival2024/?hl=en"><i class="fab fa-instagram">  National Music Festival</i></a></li>
          </ul>
          <ul class="social-icons">
            <li><a href="https://www.instagram.com/nustmusicsociety/"><i class="fab fa-instagram">  NUST Music Society</i></a></li>
          </ul>
        </div>
        <div class="footer-links">
          <h3>Quick Links</h3>
          <ul>
            <li><a href="#" @click.prevent="scrollToSection('home')">Home</a></li>
            <li><a href="#" @click.prevent="scrollToSection('schedule')">Event Schedule</a></li>
            <li><a href="#" @click.prevent="scrollToSection('participation')">Participate</a></li>
            <li><a href="#" @click.prevent="scrollToSection('registration')">Ambassador</a></li>
            <li><a href="#" @click.prevent="scrollToSection('contact')">Contact Us</a></li>
          </ul>
        </div>
        <div class="footer-contact">
          <h3>Contact Us</h3>
          <ul>
            <li><i class="fas fa-envelope"></i> nustmusicsociety23@gmail.com</li>
            <li><i class="fas fa-phone"></i> +92 331 5888763</li>
            <li><i class="fas fa-map-marker-alt"></i> NUST, H-12, Islamabad</li>
          </ul>
        </div>
      </div>
      <div class="footer-bottom">
        <p>© National Music Festival 2.0. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      logoImage: require('@/assets/logoNMF.png'),
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,
      eventDate: new Date('November 28, 2024 00:00:00').getTime(),
      menuActive: false,
      // Carousel Data
      images: [
        {
          url: require('@/assets/nmf1.png'),
          text: 'دل چھو لینے والی دھنیں'
        },
        {
          url: require('@/assets/nmf3.png'),
          text: 'آواز کی جادوگری'
        },
        {
          url: require('@/assets/nmf4.png'),
          text: 'دھڑکنوں کی تال پر'
        },
        {
          url: require('@/assets/nmf5.png'),
          text: 'موسیقی کی دنیا میں خوش آمدید'
        }
      ],

      currentImage: 0,
      // Newsletter Data
      newsletterEmail: '',
    };
  },
  created() {
    this.countdownTimer = setInterval(this.updateCountdown, 1000);
  },
  mounted() {
    this.observeElements();
  },
  methods: {
    updateCountdown() {
      const now = new Date().getTime();
      const distance = this.eventDate - now;

      if (distance < 0) {
        clearInterval(this.countdownTimer);
        this.days = this.hours = this.minutes = this.seconds = 0;
      } else {
        this.days = Math.floor(distance / (1000 * 60 * 60 * 24));
        this.hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
        this.minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
        this.seconds = Math.floor((distance % (1000 * 60)) / 1000);
      }
    },
    toggleMenu() {
      this.menuActive = !this.menuActive;
    },
    scrollToSection(sectionId) {
      this.menuActive = false;
      const element = document.getElementById(sectionId);
      if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
      }
    },
    observeElements() {
      const options = {
        threshold: 0.1,
      };
      const observer = new IntersectionObserver((entries, observer) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('visible');
            observer.unobserve(entry.target);
          }
        });
      }, options);

      const featureBoxes = document.querySelectorAll('.feature-box');
      featureBoxes.forEach(box => {
        observer.observe(box);
      });

      const days = document.querySelectorAll('.day');
      days.forEach(day => {
        observer.observe(day);
      });
    },
    // Carousel Methods
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.images.length;
    },
    prevImage() {
      this.currentImage = (this.currentImage - 1 + this.images.length) % this.images.length;
    },
    goToImage(index) {
      this.currentImage = index;
    },
    // Newsletter Subscription
    subscribeNewsletter() {
      alert(`Thank you for subscribing with ${this.newsletterEmail}!`);
      this.newsletterEmail = '';
    },
  },
  beforeUnmount() {
    clearInterval(this.countdownTimer);
  },
};
</script>

<style scoped>
/* Import Fonts and Icons */
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@400;500;700&display=swap');

/* Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* Animations */
.fade-in {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 1s ease-out, transform 1s ease-out;
}

.fade-in.visible {
  opacity: 1;
  transform: translateY(0);
}

.slide-up {
  transform: translateY(100%);
  opacity: 0;
  transition: transform 0.5s ease-out, opacity 0.5s ease-out;
}

.slide-up.visible {
  transform: translateY(0);
  opacity: 1;
}

body {
  font-family: 'Montserrat', sans-serif;
  line-height: 1.6;
  color: #333;
}

/* Container */
.container {
  width: 90%;
  max-width: 1200px;
  margin: auto;
}

/* Header Styles */
.header {
  background-color: #ffffff;
  position: sticky;
  top: 0;
  z-index: 1000;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  width: 100%;
}

.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 0;
}

.logo {
  display: flex;
  align-items: center;
}

.logo-image {
  width: 20rem; /* Adjust to desired width */
  height: auto; /* Keeps the aspect ratio */
}

.logo-image2 {
  width: 20rem; /* Adjust to desired width */
  height: auto; /* Keeps the aspect ratio */
}

.logo-text {
  display: none; /* Hidden by default */
  font-size: 1.5rem;
  font-weight: bold;
  color: #ff6f61;
}

/* Show Logo Text and Hide Image on Small Screens */
@media (max-width: 768px) {
  .logo-image {
    display: none;
  }
  .logo-text {
    display: block;
  }
}

.nav-links {
  display: flex;
  align-items: center;
}

.nav-links a {
  color: #333;
  margin-left: 1.5rem;
  text-decoration: none;
  font-size: 1.2rem;
  position: relative;
  overflow: hidden;
}

.nav-links a::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 2px;
  background: #ff6f61;
  bottom: 0;
  left: -100%;
  transition: all 0.3s ease-in-out;
}

.nav-links a:hover::after {
  left: 0;
}

.nav-links a:hover {
  color: #ff6f61;
}

.orange {
  color: #ff6f61;
}

.register-btn {
  padding: 0.5rem 1.5rem;
  background-color: #ff6f61;
  color: #fff;
  border: none;
  cursor: pointer;
  font-size: 1rem;
  margin-left: 1.5rem;
  border-radius: 5px;
  transition: background-color 0.3s ease-in-out;
}

.register-btn:hover {
  background-color: #ff5a4d;
}

.desktop-register-btn {
  display: block;
}

.mobile-register-btn {
  display: none;
}

/* Fix for Double Buy Tickets Button */
@media (min-width: 769px) {
  .mobile-register-btn {
    display: none;
  }
  .desktop-register-btn {
    display: block;
  }
}

@media (max-width: 768px) {
  .desktop-register-btn {
    display: none;
  }
  .mobile-register-btn {
    display: block;
  }
}

/* Mobile Menu Toggle */
.menu-toggle {
  display: none;
  flex-direction: column;
  width: 25px;
  cursor: pointer;
  margin-left: 1rem;
}

.menu-toggle span {
  height: 3px;
  background-color: #333;
  margin: 4px 0;
  width: 100%;
  transition: 0.3s;
}

.menu-toggle.active span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.menu-toggle.active span:nth-child(2) {
  opacity: 0;
}

.menu-toggle.active span:nth-child(3) {
  transform: rotate(-45deg) translate(5px, -5px);
}

/* Mobile Navigation */
.nav-links.nav-active {
  display: flex;
  flex-direction: column;
  position: absolute;
  background-color: #ffffff;
  top: 100%;
  left: 0;
  width: 100%;
  padding: 1rem 0;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  z-index: 999;
}

.nav-links.nav-active a {
  margin: 0.5rem 1rem;
  font-size: 1.2rem;
}

.mobile-register-btn {
  display: block;
  width: calc(100% - 2rem);
  margin: 0.5rem 1rem;
  text-align: center;
}

/* Hero Section */
.hero {
  background-image: url('https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D');
  background-size: cover;
  background-attachment: fixed;
  background-position: center;
  height: 100vh;
  color: white;
  position: relative;
}

.hero .overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.6);
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 0 2rem;
}

.hero h1 {
  font-size: calc(2rem + 2vw);
  margin-bottom: 1rem;
  animation: fadeInDown 1s forwards;
}

.hero h2 {
  font-size: calc(1.5rem + 1vw);
  margin-bottom: 1rem;
  animation: fadeInDown 1.5s forwards;
}

.hero p {
  font-size: calc(1rem + 0.5vw);
  margin-bottom: 2rem;
  animation: fadeInDown 2s forwards;
}

.hero .register-btn {
  font-size: calc(1rem + 0.5vw);
  animation: fadeInDown 2.5s forwards;
}

@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translateY(-50px);
  } to {
    opacity: 1;
    transform: translateY(0);
  }
}

.countdown {
  display: flex;
  justify-content: center;
  gap: 2rem;
  margin-top: 2rem;
  animation: fadeInUp 3s forwards;
  flex-wrap: wrap; /* Allow items to wrap to the next line */
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(50px);
  } to {
    opacity: 1;
    transform: translateY(0);
  }
}

.countdown div {
  background: rgba(255, 255, 255, 0.1);
  padding: 1rem 1.5rem;
  text-align: center;
  border-radius: 5px;
}

.countdown span {
  font-size: calc(2rem + 1vw);
  font-weight: bold;
  display: block;
}

.countdown p {
  font-size: calc(0.8rem + 0.3vw);
}

/* Responsive Adjustments for Countdown */
@media (max-width: 768px) {
  .countdown {
    gap: 1rem;
  }

  .countdown div {
    padding: 0.75rem 1rem;
  }
}

@media (max-width: 480px) {
  .countdown {
    flex-direction: column;
    align-items: center;
    gap: 0.5rem;
  }

  .countdown div {
    width: 80%;
    padding: 0.5rem 1rem;
  }

  .countdown span {
    font-size: 1.5rem;
  }

  .countdown p {
    font-size: 0.9rem;
  }
}

/* Why Join Section */
.why-join {
  padding: 4rem 0;
  text-align: center;
}

.why-join h2 {
  font-size: calc(2rem + 1vw);
  margin-bottom: 3rem;
}

.features {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
}

.feature-box {
  flex: 1 1 calc(25% - 2rem);
  margin: 1rem;
  padding: 2rem;
  background-color: #fff;
  border-radius: 10px;
  text-align: center;
  transition: transform 0.3s, box-shadow 0.3s;
  opacity: 0;
  transform: translateY(50px);
  border: 1px solid #dcdcdc;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.06);
}

.feature-box:hover {
  transform: translateY(-10px);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.12);
}

.feature-box.visible {
  opacity: 1;
  transform: translateY(0);
}

.feature-box img {
  width: 100%;
  height: auto;
  margin-bottom: 1rem;
  border-radius: 5px;
}

.feature-box h3 {
  margin-bottom: 1rem;
  font-size: calc(1.2rem + 0.5vw);
  color: #ff6f61;
}

.feature-box p {
  font-size: calc(0.9rem + 0.3vw);
}

/* Gallery Section */
.gallery {
  padding: 4rem 0;
  text-align: center;
  background-color: #fff;
}

.gallery h2 {
  font-size: calc(2rem + 1vw);
  margin-bottom: 2rem;
}

.carousel {
  position: relative;
  max-width: 100%;
  margin: auto;
  overflow: hidden;
}

.carousel-slide {
  width: 100%;
  height: 700px;
  background-size: cover;
  background-position: center;
  position: relative;
}

.carousel-text {
  position: absolute;
  bottom: 20px;
  right: 20px;
  background-color: rgba(0,0,0,0.5);
  padding: 1rem;
  border-radius: 5px;
}

.carousel-text p {
  color: #fff;
  font-size: calc(1rem + 0.5vw);
}

.carousel-controls {
  position: absolute;
  width: 100%;
  top: 50%;
  transform: translateY(-50%);
  display: flex;
  justify-content: space-between;
}

.carousel-controls .prev,
.carousel-controls .next {
  cursor: pointer;
  font-size: calc(1.5rem + 1vw);
  color: #fff;
  padding: 0 1rem;
  user-select: none;
}

.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
}

.carousel-indicators span {
  display: inline-block;
  width: 12px;
  height: 12px;
  background-color: rgba(255,255,255,0.5);
  margin: 0 5px;
  border-radius: 50%;
  cursor: pointer;
}

.carousel-indicators .active {
  background-color: #ff6f61;
}

/* Schedule Section */
.schedule {
  padding: 4rem 0;
  background-color: #f9f9f9;
  text-align: center;
}

.schedule h2 {
  font-size: calc(2rem + 1vw);
  margin-bottom: 3rem;
}

.day {
  margin-bottom: 2rem;
  opacity: 0;
  transform: translateY(50px);
  transition: opacity 1s ease-out, transform 1s ease-out;
}

.day.visible {
  opacity: 1;
  transform: translateY(0);
}

.day h3 {
  font-size: calc(1.5rem + 0.5vw);
  margin-bottom: 1rem;
  color: #ff6f61;
}

.day ul {
  list-style-type: none;
  padding: 0;
}

.day ul li {
  background-color: #fff;
  margin-bottom: 0.5rem;
  padding: 1rem;
  border-left: 5px solid #ff6f61;
}

.day ul li strong {
  font-weight: bold;
}

.day ul li:not(:last-child) {
  border-bottom: 1px solid #e0e0e0;
}

/* Participation Section */
.participation {
  padding: 4rem 0;
  text-align: center;
  background-color: #f1f1f1;
}

.participation h2 {
  font-size: calc(2rem + 1vw);
  margin-bottom: 1.5rem;
}

.participation p {
  font-size: calc(1rem + 0.5vw);
  margin-bottom: 1rem;
}

.participate-btn {
  display: inline-block;
  padding: 0.75rem 2rem;
  background-color: #ff6f61;
  color: #fff;
  text-decoration: none;
  border-radius: 5px;
  font-size: calc(1rem + 0.3vw);
  transition: background-color 0.3s ease;
}

.participate-btn:hover {
  background-color: #ff5a4d;
}

/* Registration Section */
.registration {
  position: relative;
  padding: 6rem 0;
  background-image: url('https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D');
  background-size: cover;
  background-position: center;
  color: #fff;
  text-align: center;
}

.registration::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.7);
}

.registration .overlay {
  position: relative;
  z-index: 1;
}

.registration h2 {
  font-size: calc(2.5rem + 1vw);
  margin-bottom: 1rem;
  color: #ff6f61;
}

.registration h3 {
  font-size: calc(1.8rem + 0.5vw);
  margin-bottom: 1.5rem;
}

.registration p {
  font-size: calc(1rem + 0.5vw);
  margin-bottom: 2rem;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.registration .register-btn {
  font-size: calc(1rem + 0.5vw);
  padding: 0.75rem 2rem;
  background-color: #ff6f61;
  border: none;
  border-radius: 5px;
  color: #fff;
  transition: background-color 0.3s ease;
  cursor: pointer;
}

.registration .register-btn:hover {
  background-color: #ff5a4d;
}

/* Adjusting z-index for other elements */
.registration, .registration .overlay {
  position: relative;
  z-index: 1;
}

/* Footer */
footer {
  background-color: #1a1a1a;
  color: #fff;
  padding-top: 2rem;
}

.footer-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
  padding-bottom: 2rem;
}

.footer-about,
.footer-links,
.footer-contact,
.footer-newsletter {
  flex: 1 1 200px;
  margin: 1rem;
}

.footer-about h2 {
  font-size: calc(1.5rem + 0.5vw);
  margin-bottom: 1rem;
}

.footer-about p {
  font-size: calc(0.9rem + 0.3vw);
  max-width: 300px;
  margin-bottom: 1rem;
}

.social-icons {
  list-style: none;
  display: flex;
  margin-top: 1rem;
}

.social-icons li {
  margin-right: 1rem;
}

.social-icons li a {
  color: #fff;
  font-size: calc(1.0rem + 0.1vw);
  transition: color 0.3s;
}

.social-icons li a:hover {
  color: #ff6f61;
}

.footer-links h3,
.footer-contact h3,
.footer-newsletter h3 {
  font-size: calc(1.2rem + 0.3vw);
  margin-bottom: 1rem;
}

.footer-links ul,
.footer-contact ul {
  list-style-type: none;
}

.footer-links ul li,
.footer-contact ul li {
  margin-bottom: 0.5rem;
}

.footer-links ul li a {
  color: #fff;
  text-decoration: none;
}

.footer-links ul li a:hover {
  color: #ff6f61;
}

.footer-contact ul li {
  display: flex;
  align-items: center;
}

.footer-contact ul li i {
  margin-right: 0.5rem;
}

.footer-newsletter p {
  font-size: calc(0.9rem + 0.3vw);
  margin-bottom: 1rem;
}

.footer-newsletter form {
  display: flex;
}

.footer-newsletter input[type="email"] {
  flex: 1;
  padding: 0.5rem;
  border: none;
  border-radius: 5px 0 0 5px;
  font-size: calc(0.9rem + 0.3vw);
}

.footer-newsletter button {
  padding: 0.5rem 1rem;
  background-color: #ff6f61;
  color: #fff;
  border: none;
  border-radius: 0 5px 5px 0;
  cursor: pointer;
  font-size: calc(0.9rem + 0.3vw);
}

.footer-newsletter button:hover {
  background-color: #ff5a4d;
}

.footer-bottom {
  background-color: #111;
  text-align: center;
  padding: 1rem 0;
  font-size: calc(0.8rem + 0.2vw);
}

.footer-bottom p {
  margin: 0;
}

/* Responsive Styles */
@media (max-width: 1200px) {
  #hero-heading{
    padding-top: 5rem;
  }
  .feature-box {
    flex: 1 1 calc(50% - 2rem);
  }
}

@media (max-width: 768px) {
  .none-sm{
    display: none;
  }
  #hero-heading{
    padding-top: 6rem;
  }
  .nav {
    flex-wrap: wrap;
  }

  .nav-links,
  .desktop-register-btn {
    display: none;
  }

  .menu-toggle {
    display: flex;
  }

  .nav-links.nav-active {
    display: flex;
  }

  .features {
    flex-direction: column;
    align-items: center;
  }

  .feature-box {
    flex: 1 1 100%;
    margin: 1rem 0;
  }

  .footer-container {
    flex-direction: column;
    align-items: center;
  }

  .footer-about,
  .footer-links,
  .footer-contact,
  .footer-newsletter {
    margin: 1rem 0;
  }

  .footer-newsletter form {
    flex-direction: column;
  }

  .footer-newsletter input[type="email"] {
    border-radius: 5px;
    margin-bottom: 1rem;
  }

  .footer-newsletter button {
    border-radius: 5px;
  }

  .carousel-slide {
    height: 300px;
  }

  .countdown {
    flex-direction: column;
    gap: 1rem;
  }

  .countdown div {
    padding: 0.5rem 1rem;
  }

  .day ul li {
    font-size: calc(0.9rem + 0.3vw);
  }
}

@media (max-width: 480px) {
  .none-sm{
    display: none;
  }
  .hero h1 {
    font-size: calc(1.8rem + 2vw);
  }
  #hero-heading{
    padding-top: 10rem;
  }


  .hero h2 {
    font-size: calc(1.2rem + 1vw);
  }

  .hero p {
    font-size: calc(0.9rem + 0.5vw);
  }

  .feature-box h3 {
    font-size: calc(1rem + 0.5vw);
  }

  .feature-box p {
    font-size: calc(0.8rem + 0.3vw);
  }

  .carousel-text p {
    font-size: calc(0.9rem + 0.5vw);
  }

  .day h3 {
    font-size: calc(1.2rem + 0.5vw);
  }

  .participation h2 {
    font-size: calc(1.5rem + 1vw);
  }

  .participation p {
    font-size: calc(0.9rem + 0.5vw);
  }

  .participate-btn {
    font-size: calc(0.9rem + 0.3vw);
  }

  .registration h2 {
    font-size: calc(2rem + 1vw);
  }

  .registration h3 {
    font-size: calc(1.5rem + 0.5vw);
  }

  .registration p {
    font-size: calc(0.9rem + 0.5vw);
  }

  .registration .register-btn {
    font-size: calc(0.9rem + 0.5vw);
  }

  .footer-about h2,
  .footer-links h3,
  .footer-contact h3 {
    font-size: calc(1.2rem + 0.5vw);
  }

  .footer-about p,
  .footer-contact ul li,
  .footer-links ul li a {
    font-size: calc(0.8rem + 0.3vw);
  }
}
@font-face {
  font-family: 'YourCustomFont';
  src: url('@/assets/Jameel Noori Nastaleeq Kasheeda.ttf') format('truetype');
  font-weight: normal;
  font-style: normal;
}
/* Apply custom font to the hero heading */
#hero-heading {
  font-family: 'YourCustomFont', sans-serif;
}

</style>
