<template>
  <section class="hero-content" id="home">
    <div class="container">
      <Nav />
    </div>
    <img class="heroLogo" src="../../public/Cvsi.svg" alt="Canvesi" />
    <h1>Wir gestalten die digitale Zukunft.</h1>
    <p>
      Wir entwerfen und implementieren fortschrittliche Webplattformen, die
      Ästhetik mit höchster Funktionalität verbinden und das Wachstum Ihres
      Unternehmens im Internet vorantreiben.
    </p>
    <a href="#contact" class="cta-button">Starten Sie Ihr Projekt</a>
  </section>
</template>
<script>
import Nav from "./Nav.vue";

export default {
  name: "HeroSection",
  components: {
    Nav,
  },
};
</script>

<style scoped>
.heroLogo {
  width: 100%;
  height: auto;
  max-width: 600px;
  margin: 0;
  display: block;
}
.hero-content {
  position: relative;
  width: 100vw;
  z-index: 10;
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: #fff;
  padding: 0 40px;
  margin: 0 auto;
  pointer-events: none;
}

.hero-content h1 {
  font-size: clamp(2.5rem, 7vw, 5rem);
  margin-bottom: 2rem;
  line-height: 1.1;
  text-shadow: 0 0 15px rgba(102, 224, 255, 0.8),
    0 0 30px rgba(102, 224, 255, 0.6);
  pointer-events: auto;
  margin-top: 1rem;
}

.hero-content p {
  font-size: clamp(1.1rem, 2.5vw, 1.6rem);
  max-width: 800px;
  margin-bottom: 40px;
  opacity: 0.9;
  line-height: 1.5;
  color: #e0e0e0;
  text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.8), 2px 2px 6px rgba(0, 0, 0, 0.6);
  pointer-events: auto;
}
.cta-button {
  display: inline-block;
  padding: 15px 35px;

  background-color: transparent;
  border: 2px solid #e0e0e0;
  color: #3a677e;
  font-size: 1.2rem;
  font-weight: bold;
  text-decoration: none;
  border-radius: 50px;
  transition: all 0.2s ease;
  box-shadow: 0 0 15px rgba(102, 224, 255, 0.8),
    0 0 30px rgba(102, 224, 255, 0.6);
  pointer-events: auto;
  background-color: #fce7cd;
}

.cta-button:hover {
  background-color: rgba(255, 140, 0, 0.8);
  box-shadow: 0 0 25px rgba(255, 140, 0, 0.8), 0 0 40px rgba(255, 140, 0, 0.6);
  transform: translateY(-3px);
  color: #fff;
  text-shadow: 0 0 25px rgba(255, 140, 0, 0.8), 0 0 40px rgba(255, 140, 0, 0.6);
}
</style>
