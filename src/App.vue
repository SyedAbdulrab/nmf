<template>
  <div id="app">
    <!-- Header -->
    <header class="header">
      <div class="nav container">
        <div class="logo">National Music Festival</div>
        <div class="nav-links" :class="{ 'nav-active': menuActive }">
          <a href="#home" @click="scrollToSection('home')">Home</a>
          <a href="#schedule" @click="scrollToSection('schedule')">Event Schedule</a>
          <a href="#participation" @click="scrollToSection('participation')">Participate</a>
          <a href="#registration" @click="scrollToSection('registration')">Volunteer Registration</a>
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
        <h1>دل کی دھڑکنوں کو <span class="orange">موسیقی</span> کے ساتھ ملائیں</h1>
        <h2>National Music Festival 2024</h2>
        <p>NUST, H-12, Islamabad | 13-15 December 2024</p>
        <a href="https://docs.google.com/forms/d/e/1FAIpQLSewJKQbnhNKDRAmlVwEbYqJF4P2pIZWu5h9x2VLkY6AA9A-yw/viewform?usp=sf_link">
        <button class="register-btn">Buy Tickets</button>
      </a>
        <div class="countdown">
          <div>
            <span>{{ days }}</span>
            <p>Days</p>
          </div>
          <div>
            <span>{{ hours }}</span>
            <p>Hours</p>
          </div>
          <div>
            <span>{{ minutes }}</span>
            <p>Minutes</p>
          </div>
          <div>
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
          <img src="https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" alt="Live Performances">
          <h3>Live Performances</h3>
          <p>Enjoy electrifying performances from top artists and bands.</p>
        </div>
        <div class="feature-box">
          <img src="https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" alt="Music Workshops">
          <h3>Music Workshops</h3>
          <p>Participate in workshops and learn from industry professionals.</p>
        </div>
        <div class="feature-box">
          <img src="https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" alt="Networking">
          <h3>Networking</h3>
          <p>Connect with fellow music enthusiasts and expand your network.</p>
        </div>
        <div class="feature-box">
          <img src="https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D" alt="Food & Fun">
          <h3>Food & Fun</h3>
          <p>Indulge in delicious food and enjoy various fun activities.</p>
        </div>
      </div>
    </section>

    <!-- Gallery Section -->
    <section class="gallery" id="gallery">
      <h2>موسیقی کے <span class="orange">رنگ</span></h2>
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
      <h2>
<span class="orange">        موسیقی
  کے میلے

</span>
         کا حصہ بنیں</h2>
      <p>Are you an artist, musician, or performer looking to showcase your talent?</p>
      <p>Join us at the National Music Festival 2024!</p>
      <a href="https://docs.google.com/forms/d/e/1FAIpQLSfiUXOCB_fd06rYBHMrMCsT6-BfY7Mje5BNVH8R_CGdlunvWA/viewform?usp=sf_link" target="_blank" class="participate-btn">Participate Now</a>
    </section>

    <!-- Schedule Section -->
    <section class="schedule" id="schedule">
      <h2>Event Schedule</h2>
      <div class="days container">
        <div class="day">
          <h3>Day 1 - Dec 13, 2024</h3>
          <ul>
            <li><strong>Opening Ceremony</strong> - Special Guest Appearance</li>
            <li><strong>Rock Concert</strong> - Featuring Local Bands</li>
            <li><strong>DJ Night</strong> - Dance to the Beats</li>
          </ul>
        </div>
        <div class="day">
          <h3>Day 2 - Dec 14, 2024</h3>
          <ul>
            <li><strong>Classical Performances</strong> - Renowned Musicians</li>
            <li><strong>Music Workshops</strong> - Learn and Grow</li>
            <li><strong>Battle of the Bands</strong> - Witness Talent</li>
          </ul>
        </div>
        <div class="day">
          <h3>Day 3 - Dec 15, 2024</h3>
          <ul>
            <li><strong>Grand Finale Concert</strong> - International Artists</li>
            <li><strong>Awards Ceremony</strong> - Honoring Excellence</li>
            <li><strong>Closing Ceremony</strong> - Fireworks Display</li>
          </ul>
        </div>
      </div>
    </section>

    <!-- Registration Section -->
    <section class="registration" id="registration">
      <div class="overlay">
        <h2>
Get your tickets Now
        </h2>
        <h3>
<span class="orange">          موسیقی کے میلے
</span>
          کا حصہ بنیں
        </h3>
        <p>
Become a part of the greatest music festival that NUST has ever witnessed since ON'21. Let's make history together!
        </p>
        <a href="https://docs.google.com/forms/d/e/1FAIpQLSewJKQbnhNKDRAmlVwEbYqJF4P2pIZWu5h9x2VLkY6AA9A-yw/viewform?usp=sf_link" target="_blank">
          <button class="register-btn">
Get tickets        </button>
        </a>
      </div>
    </section>

    <!-- Contact Section
    <section class="contact" id="contact">
      <h2>Contact Us</h2>
      <p>If you have any questions, feel free to reach out to us.</p>
      <p>Email: info@musicfestival.pk</p>
      <p>Phone: +92 123 4567890</p>
    </section> -->

    <!-- Footer -->
    <footer>
      <div class="footer-container container">
        <div class="footer-about">
          <h2>National Music Festival</h2>
          <p>Bringing together music lovers from all over the country.</p>
          <ul class="social-icons">
            <li><a href="#"><i class="fab fa-facebook-f"></i></a></li>
            <li><a href="#"><i class="fab fa-twitter"></i></a></li>
            <li><a href="#"><i class="fab fa-instagram"></i></a></li>
            <li><a href="#"><i class="fab fa-youtube"></i></a></li>
          </ul>
        </div>
        <div class="footer-links">
          <h3>Quick Links</h3>
          <ul>
            <li><a href="#" @click.prevent="scrollToSection('home')">Home</a></li>
            <li><a href="#" @click.prevent="scrollToSection('schedule')">Event Schedule</a></li>
            <li><a href="#" @click.prevent="scrollToSection('participation')">Participate</a></li>
            <li><a href="#" @click.prevent="scrollToSection('registration')">Volunteer Registration</a></li>
            <li><a href="#" @click.prevent="scrollToSection('contact')">Contact Us</a></li>
          </ul>
        </div>
        <div class="footer-contact">
          <h3>Contact Us</h3>
          <ul>
            <li><i class="fas fa-envelope"></i> info@musicfestival.pk</li>
            <li><i class="fas fa-phone"></i> +92 123 4567890</li>
            <li><i class="fas fa-map-marker-alt"></i> NUST, H-12, Islamabad</li>
          </ul>
        </div>
        <!-- <div class="footer-newsletter">
          <h3>Newsletter</h3>
          <p>Subscribe to our newsletter to get the latest updates.</p>
          <form @submit.prevent="subscribeNewsletter">
            <input type="email" v-model="newsletterEmail" placeholder="Enter your email" required>
            <button type="submit">Subscribe</button>
          </form>
        </div> -->
      </div>
      <div class="footer-bottom">
        <p>© 2024 National Music Festival. All rights reserved.</p>
      </div>
    </footer>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,
      eventDate: new Date('December 13, 2024 00:00:00').getTime(),
      menuActive: false,
      // Carousel Data
      images: [
        {
          url: 'https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
          text: 'دل چھو لینے والی دھنیں',
        },
        {
          url: 'https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
          text: 'سر اور تال کا سنگم',
        },
        {
          url: 'https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
          text: 'آواز کی جادوگری',
        },
        {
          url: 'https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
          text: 'دھڑکنوں کی تال پر',
        },
        {
          url: 'https://images.unsplash.com/photo-1514320291840-2e0a9bf2a9ae?q=80&w=3540&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
          text: 'موسیقی کی دنیا میں خوش آمدید',
        },
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
}

.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 0;
}

.logo {
  font-size: 1.8rem;
  color: #ff6f61;
  font-weight: 700;
}

.nav-links {
  display: flex;
  align-items: center;
}

.nav-links a {
  color: #333;
  margin-left: 1.5rem;
  text-decoration: none;
  font-size: 1rem;
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

/* Adjustments for smaller screens */
  .hero h1 {
    font-size: 2.5rem;
  }

  .hero h2 {
    font-size: 1.8rem;
  }

  .hero p {
    font-size: 1rem;
  }

  .hero .countdown div {
    padding: 0.5rem 1rem;
  }

  .features {
    flex-direction: column;
    align-items: center;
  }

  .feature-box {
    flex: 1 1 100%;
    margin: 1rem 0;
  }

  /* Responsive Carousel */
  .carousel-slide {
    height: 300px;
  }

  .carousel-text p {
    font-size: 1rem;
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
  font-size: 3.5rem;
  margin-bottom: 1rem;
  animation: fadeInDown 1s forwards;
}

.hero h2 {
  font-size: 2.5rem;
  margin-bottom: 1rem;
  animation: fadeInDown 1.5s forwards;
}

.hero p {
  font-size: 1.5rem;
  margin-bottom: 2rem;
  animation: fadeInDown 2s forwards;
}

.hero .register-btn {
  font-size: 1.2rem;
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
  font-size: 2.5rem;
  font-weight: bold;
  display: block;
}

.countdown p {
  font-size: 1rem;
}

/* Why Join Section */
.why-join {
  padding: 4rem 0;
  text-align: center;
}

.why-join h2 {
  font-size: 2.5rem;
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
  font-size: 1.5rem;
  color: #ff6f61;
}

.feature-box p {
  font-size: 1rem;
}

/* Gallery Section */
.gallery {
  padding: 4rem 0;
  text-align: center;
  background-color: #fff;
}

.gallery h2 {
  font-size: 2.5rem;
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
  height: 500px;
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
  font-size: 1.5rem;
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
  font-size: 2rem;
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
  font-size: 2.5rem;
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
  font-size: 2rem;
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
  font-size: 2.5rem;
  margin-bottom: 1.5rem;
}

.participation p {
  font-size: 1.2rem;
  margin-bottom: 1rem;
}

.participate-btn {
  display: inline-block;
  padding: 0.75rem 2rem;
  background-color: #ff6f61;
  color: #fff;
  text-decoration: none;
  border-radius: 5px;
  font-size: 1.2rem;
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
  font-size: 3rem;
  margin-bottom: 1rem;
  color: #ff6f61;
}

.registration h3 {
  font-size: 2rem;
  margin-bottom: 1.5rem;
}

.registration p {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.registration .register-btn {
  font-size: 1.5rem;
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

/* Contact Section */
.contact {
  padding: 4rem 0;
  text-align: center;
  background-color: #f9f9f9;
}

.contact h2 {
  font-size: 2.5rem;
  margin-bottom: 2rem;
}

.contact p {
  font-size: 1.2rem;
  margin-bottom: 1rem;
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
  font-size: 1.8rem;
  margin-bottom: 1rem;
}

.footer-about p {
  font-size: 1rem;
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
  font-size: 1.5rem;
  transition: color 0.3s;
}

.social-icons li a:hover {
  color: #ff6f61;
}

.footer-links h3,
.footer-contact h3,
.footer-newsletter h3 {
  font-size: 1.5rem;
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
  font-size: 1rem;
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
  font-size: 1rem;
}

.footer-newsletter button {
  padding: 0.5rem 1rem;
  background-color: #ff6f61;
  color: #fff;
  border: none;
  border-radius: 0 5px 5px 0;
  cursor: pointer;
  font-size: 1rem;
}

.footer-newsletter button:hover {
  background-color: #ff5a4d;
}

.footer-bottom {
  background-color: #111;
  text-align: center;
  padding: 1rem 0;
  font-size: 0.9rem;
}

.footer-bottom p {
  margin: 0;
}

/* Responsive Styles */
@media (max-width: 768px) {
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
}
</style>
