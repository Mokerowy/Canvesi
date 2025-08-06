<template>
  <nav class="compas-container">
    <i
      class="fa-regular fa-compass compas"
      aria-hidden="true"
      ref="compasElement"
    ></i>

    <ul class="miniNav" ref="miniNavElement">
      <li><a href="#home">Start Seite</a></li>
      <li><a href="#about">ÜberUns</a></li>
      <li><a href="#services">Leistungen</a></li>
      <li><a href="#price">Preise</a></li>
      <li><a href="#contact">Kontakt</a></li>
    </ul>
  </nav>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const compasElement = ref(null);
const miniNavElement = ref(null);
let hideTimeout = null;
const HIDE_DELAY = 300;
const MOBILE_BREAKPOINT = 768;

const isMobileView = window.innerWidth <= MOBILE_BREAKPOINT;

const closeMiniNav = () => {
  if (!miniNavElement.value) return;
  miniNavElement.value.classList.remove("is-visible");
  compasElement.value?.classList.remove("is-rotated");
  clearTimeout(hideTimeout);
};

const showMiniNav = () => {
  if (!miniNavElement.value) return;
  clearTimeout(hideTimeout);
  miniNavElement.value.classList.add("is-visible");
  compasElement.value?.classList.add("is-rotated");
};

const handleMouseEnter = () => {
  if (!isMobileView) {
    showMiniNav();
  }
};

const handleMouseLeave = () => {
  if (!isMobileView) {
    hideTimeout = setTimeout(closeMiniNav, HIDE_DELAY);
  }
};

const handleCompasClick = (event) => {
  event.stopPropagation();
  if (miniNavElement.value?.classList.contains("is-visible")) {
    closeMiniNav();
  } else {
    showMiniNav();
  }
};

const handleClickOutside = (event) => {
  const isClickInside =
    compasElement.value?.contains(event.target) ||
    miniNavElement.value?.contains(event.target);
  if (!isClickInside) {
    closeMiniNav();
  }
};

const handleNavLinkClick = (event) => {
  event.preventDefault();
  const targetId = event.currentTarget.getAttribute("href");
  const targetSection = document.querySelector(targetId);

  if (targetSection) {
    const offset = 80;
    const scrollToPosition = targetSection.offsetTop - offset;
    window.scrollTo({
      top: scrollToPosition,
      behavior: "smooth",
    });
  }
  closeMiniNav();
};

const handleResize = () => {
  if (window.innerWidth <= MOBILE_BREAKPOINT) {
    closeMiniNav();
  }
};

onMounted(() => {
  window.addEventListener("resize", handleResize);
  document.addEventListener("click", handleClickOutside);

  compasElement.value.addEventListener("mouseenter", handleMouseEnter);
  compasElement.value.addEventListener("mouseleave", handleMouseLeave);
  compasElement.value.addEventListener("click", handleCompasClick);

  miniNavElement.value.addEventListener("mouseenter", handleMouseEnter);
  miniNavElement.value.addEventListener("mouseleave", handleMouseLeave);

  miniNavElement.value.querySelectorAll('a[href^="#"]').forEach((link) => {
    link.addEventListener("click", handleNavLinkClick);
  });
});

onBeforeUnmount(() => {
  clearTimeout(hideTimeout);
  window.removeEventListener("resize", handleResize);
  document.removeEventListener("click", handleClickOutside);

  compasElement.value.removeEventListener("mouseenter", handleMouseEnter);
  compasElement.value.removeEventListener("mouseleave", handleMouseLeave);
  compasElement.value.removeEventListener("click", handleCompasClick);

  miniNavElement.value.removeEventListener("mouseenter", handleMouseEnter);
  miniNavElement.value.removeEventListener("mouseleave", handleMouseLeave);

  miniNavElement.value.querySelectorAll('a[href^="#"]').forEach((link) => {
    link.removeEventListener("click", handleNavLinkClick);
  });
});
</script>

<style scoped>
.compas-container {
  position: fixed;
  z-index: 30;
}

.compas {
  position: fixed;
  color: #80d4ff;
  cursor: pointer;
  transition: transform 0.6s ease, color 0.3s ease, opacity 0.3s ease;
  z-index: 5;
  opacity: 0.6;
  display: none;
  z-index: 30;
}

.compas.is-rotated {
  scale: 1.1;
  transform: rotate(160deg);
  opacity: 1;
}

.miniNav {
   display: flex;
  position: fixed;
  right: -550px;
  border: solid 2px #80d4ff;
  color: #80d4ff;
height: 100vh;
  visibility: hidden;
  pointer-events: none;
  transition: opacity 0.4s ease-out, visibility 0.4s ease-out,
    right 0.4s ease-out;
  z-index: 3;
  text-shadow: 0 0 8px rgba(128, 212, 255, 0.7),
    0 0 15px rgba(128, 212, 255, 0.5), 0 0 25px rgba(128, 212, 255, 0.3);
}

.miniNav.is-visible {
  opacity: 1;
  visibility: visible;
  right: 110px;
  pointer-events: auto;
}

.miniNav a {
  color: #80d4ff;
  text-decoration: none;
  transition: color 0.1s ease, text-shadow 0.3s ease;
  white-space: nowrap;
}

.miniNav a:hover {
  color: #ffffff;
  text-shadow: 0 0 10px #fff, 0 0 20px rgba(255, 255, 255, 0.8),
    0 0 40px rgba(255, 255, 255, 0.6);
}

@media (max-width: 899px) {
  .compas {
    top: 20px;
    right: 20px;
    font-size: 2.5rem;
    display: block;
  }

  .miniNav {
    top: 0;
    right: -100vw;
    width: 100vw;
   
    padding: 80px 20px 20px 20px;

    background-color: rgba(26, 21, 18, 0.95);

    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    gap: 30px;
    font-size: 2rem;
  }

  .miniNav.is-visible {
    right: 0;
  }

  .miniNav a {
    text-align: center;
  }
}
</style>
