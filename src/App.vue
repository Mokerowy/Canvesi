<template>
  <div id="app">
    <div class="heroImage"></div>

    <Canvas aria-hidden="true" />
    <video
      aria-hidden="true"
      autoplay
      muted
      playsinline
      class="dust"
      id="video1"
      src="../public/5561385-uhd_3840_2160_25fps.mp4"
      ref="video1Element"
    ></video>
    <video
      aria-hidden="true"
      muted
      playsinline
      class="dust"
      id="video2"
      src="../public/marsdust.mp4"
      ref="video2Element"
    ></video>

    <main class="content-wrapper">
      <HeroSection />
      <MiniNavbar />
      <AboutSection />
      <ServicesSection />
      <Price />
     
      <ContactSection />
    </main>
  </div>
</template>
<script>
import { ref, onMounted, onBeforeUnmount } from "vue";

import HeroSection from "./components/HeroSection.vue";
import MiniNavbar from "./components/MiniNavbar.vue";
import AboutSection from "./components/AboutSection.vue";
import ServicesSection from "./components/ServicesSection.vue";

import ContactSection from "./components/ContactSection.vue";
import Canvas from "./components/Canvas.vue";
import Price from "./components/Price.vue";    


export default {
  name: "App",
  components: {
    HeroSection,
    MiniNavbar,
    AboutSection,
    ServicesSection,
    
    ContactSection,
    Canvas,
    Price,
  },
  setup() {
    const video1Element = ref(null);
    const video2Element = ref(null);

    const handleVideo1Ended = () => {
      if (video1Element.value && video2Element.value) {
        video1Element.value.style.display = "none";
        video2Element.value.style.display = "block";
        video2Element.value.currentTime = 0;
        video2Element.value
          .play()
          .catch((error) => console.error("Error playing video2:", error));
      }
    };

    const handleVideo2Ended = () => {
      if (video1Element.value && video2Element.value) {
        video2Element.value.style.display = "none";
        video1Element.value.style.display = "block";
        video1Element.value.currentTime = 0;
        video1Element.value
          .play()
          .catch((error) => console.error("Error playing video1:", error));
      }
    };

    onMounted(() => {
      if (video1Element.value && video2Element.value) {
        video2Element.value.style.display = "none";

        video1Element.value.play().catch((error) => {
          console.warn(
            "Autoplay for video1 blocked. User interaction might be required.",
            error
          );
        });

        video1Element.value.addEventListener("ended", handleVideo1Ended);
        video2Element.value.addEventListener("ended", handleVideo2Ended);
      }
    });

    onBeforeUnmount(() => {
      if (video1Element.value) {
        video1Element.value.removeEventListener("ended", handleVideo1Ended);
        video1Element.value.pause();
      }
      if (video2Element.value) {
        video2Element.value.removeEventListener("ended", handleVideo2Ended);
        video2Element.value.pause();
      }
    });

    return {
      video1Element,
      video2Element,
    };
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

html {
  scroll-behavior: smooth;
}

body {
  font-family: Arial, sans-serif;
  color: #333;
  overflow-x: hidden;
  background-color: #0d0d0d;
}

.heroImage {
  position: fixed;
  background-image: url("../public/mars.png");
  background-size: cover;
  background-position: center;
  height: 100vh;
  width: 100%;
  z-index: 0;
}

.dust {
  position: fixed;
  top: 0;
  right: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  z-index: 1;
  opacity: 0.2;
}

.section {
  text-align: center;
  position: relative;
  z-index: 5;
  padding: 5rem 2.5rem; 
  background-color: rgba(29, 28, 28, 0.95);
  color: rgb(255, 255, 255);
  line-height: 1.7;
  font-size: 1.15rem;
  letter-spacing: 0.02em;
}

.section h2 {
  font-size: clamp(2rem, 5vw, 3.5rem);
  margin-bottom: 2.5rem; 
  color: rgb(255, 255, 255);
  text-shadow: 0 0 10px rgba(102, 224, 255, 0.7);
  line-height: 1.2;
}

.section h3 {
  font-size: clamp(1.5rem, 3vw, 2.5rem);
  margin-top: 3rem; 
  margin-bottom: 1.5rem; 
  color: rgb(170, 230, 255);
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.section p {
  font-size: 1.1rem;
  margin-bottom: 1.5rem; 
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
  opacity: 0.9;
}

.section ul {
  list-style: none;
  padding: 0;
  margin: 2.5rem auto; 
  max-width: 700px;
  text-align: left;
}

.section ul li {
  font-size: 1.1rem;
  margin-bottom: 1rem; 
  padding-left: 1.5rem; 
  position: relative;
  line-height: 1.6;
}

.section ul li::before {
  content: "⚡";
  color: rgb(255, 255, 255);
  position: absolute;
  left: 0;
  top: 0;
  font-size: 1.2em;
  line-height: 1.6;
}

.section a {
  color: rgb(200, 240, 255);
  text-decoration: none;
  border-bottom: 1px solid rgb(200, 240, 255); 
  transition: all 0.3s ease;
}

.section a:hover {
  color: rgb(255, 255, 255);
  border-bottom-color: rgb(255, 255, 255);
  text-shadow: 0 0 5px rgba(255, 255, 255, 0.5);
}

.section p strong {
  color: rgb(255, 255, 255);
  text-shadow: 0 0 5px rgba(102, 224, 255, 0.5);
}

@media (max-width: 768px) {
  .section {
    padding: 60px 25px;
  }

  .section h2 {
    margin-bottom: 30px;
  }

  .section h3 {
    margin-top: 40px;
    margin-bottom: 20px;
  }

  .section ul {
    margin: 30px auto;
  }
}
</style>
