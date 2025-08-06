<template>
  <nav class="navbar" ref="Nav">
    <ul>
      <li class="logoPosition">
        <a class="logoLink" href="#home" aria-label="Gehe zur Startseite" @click="handleNavLinkClick">
          <img class="logo" src="../../public/Canvesi.svg" alt="Logo der Firma Canvesi" />
          <img class="logoName" src="../../public/Cvsi.svg" alt="Canvesi" />
        </a>
      </li>
      <li><a class="nav-link" href="#about" @click="handleNavLinkClick">Über Uns</a></li>
      <li><a class="nav-link" href="#services" @click="handleNavLinkClick">Leistungen</a></li>
      <li><a class="nav-link" href="#price" @click="handleNavLinkClick">Preise</a></li>
      <!-- <li><a class="nav-link" href="#portfolio" @click="handleNavLinkClick">Portfolio</a></li> -->
      <li><a class="nav-link contactLink" href="#contact" @click="handleNavLinkClick">Kontakt</a></li>
    </ul>
  </nav>
</template>

<script setup>


const handleNavLinkClick = (event) => {
  event.preventDefault(); 
  const targetId = event.currentTarget.getAttribute("href");
  const targetSection = document.querySelector(targetId);

  if (targetSection) {
    const offset = 90; 
    const scrollToPosition = targetSection.offsetTop - offset;

    window.scrollTo({
      top: scrollToPosition,
      behavior: "smooth",
    });
  }
};


</script>

<style>
a {
  text-decoration: none;
}

.logoLink {
  display: flex;
  align-items: center;
  justify-content: center;
  color: rgb(0, 0, 0);
  pointer-events: auto;
  margin-left: 50px;
}

.logoLink:hover .logoName,
.logoLink:hover .logo {
  opacity: 1;
}

.logo {
  transform: scaleX(-1);

  width: 3.125rem;
  height: 3.125rem;
  border-radius: 100%;
  box-shadow: inset 0 0 0.5rem rgba(128, 212, 255, 0.7),
    inset 0 0 0.9375rem rgba(128, 212, 255, 0.5),
    inset 0 0 1.5625rem rgba(128, 212, 255, 0.3),
    0 0 0.5rem rgba(128, 212, 255, 0.7), 0 0 0.9375rem rgba(128, 212, 255, 0.5),
    0 0 1.5625rem rgba(128, 212, 255, 0.3);
  opacity: 0.8;
  cursor: pointer;
  z-index: 100;
  margin-left: 3.125rem;
}

.logoName {
  opacity: 0.8;
  margin-right: 3.125rem;
  height: 3.125rem;
  shape-rendering: geometricPrecision;
}

.navbar {
  background-color: rgba(4, 4, 8, 0.96);
  width: 100vw;
  height: 90px;
  position: fixed;
  top: 0;
  left: 0;
  display: flex;
  align-items: center;
  margin: 0 auto;
  z-index: 20;
  box-shadow: inset 0 0 10px rgba(255, 255, 255, 0.1),
    0 0 20px rgba(0, 0, 0, 0.5), 0 0 30px rgba(0, 0, 0, 0.3);
  display: none;
}

.navbar ul {
  display: flex;
  list-style: none;
  justify-content: space-around;
  width: 100%;
  align-items: center;
}

.contactLink {
  margin-right: 20px;
}

.nav-link {
  color: #80d4ff;
  text-shadow: 0 0 8px rgba(128, 212, 255, 0.7),
    0 0 15px rgba(128, 212, 255, 0.5), 0 0 25px rgba(128, 212, 255, 0.3);
  font-size: 1.5rem;
  font-weight: 700;
  text-decoration: none;
  transition: background 0.2s, color 0.2s, text-shadow 0.2s, filter 0.2s;
  display: block;
  animation: hologram-pulse 2s infinite ease-in-out alternate;
  pointer-events: auto;
}

.nav-link:hover {
  color: #fff;
  text-shadow: 0 0 10px #fff, 0 0 20px rgba(255, 255, 255, 0.8),
    0 0 40px rgba(255, 255, 255, 0.6);
  animation: none;
  filter: brightness(1.5) contrast(1.5);
  scale: 1.05;
}

@keyframes hologram-pulse {
  0% {
    opacity: 0.9;
    transform: scale(1) translateY(0);
    text-shadow: 0 0 8px rgba(102, 224, 255, 0.7),
      0 0 15px rgba(102, 224, 255, 0.5), 0 0 25px rgba(102, 224, 255, 0.3);
  }
  50% {
    opacity: 1;
    transform: scale(1.01) translateY(-1px);
    text-shadow: 0 0 10px rgba(102, 224, 255, 0.8),
      0 0 20px rgba(102, 224, 255, 0.6), 0 0 35px rgba(102, 224, 255, 0.4);
  }
  100% {
    opacity: 0.9;
    transform: scale(1) translateY(0);
    text-shadow: 0 0 8px rgba(102, 224, 255, 0.7),
      0 0 15px rgba(102, 224, 255, 0.5), 0 0 25px rgba(102, 224, 255, 0.3);
  }
}

@media (min-width: 900px) and (min-height: 710px) {
  .navbar {
    display: flex;
  }
  .contactLink {
    margin-right: 40px;
  }
  .logoLink {
    margin-left: 20px;
  }
}

@media (min-width: 1000px) {
  .logoName {
    font-size: 2.5rem;
    display: block;
  }
  .navbar a {
    font-size: 1.5rem;
  }
}

@media (min-width: 1200px) {
  .navbar a {
    font-size: 1.6rem;
  }
  .contactLink {
    margin-right: 100px;
  }
}

@media (min-width: 1324px) {
  .navbar a {
    font-size: 2rem;
  }
  .contactLink {
    margin-right: 150px;
  }
  .logo {
    width: 60px;
    height: 60px;
    margin-left: 100px;
  }
}

@media (min-width: 1600px) {
  .contactLink {
    margin-right: 250px;
  }
}
</style>
