<template>
  <canvas id="canvas1" ref="canvasElement"></canvas>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";

const canvasElement = ref(null);
let ctx = null;
const particlesArray = ref([]); 
let animationFrameId = null;

const marsColors = [
  "rgba(150, 112, 54, 0.27)",
  "rgba(230, 153, 52, 0.1)",
  "rgba(204, 125, 34, 0.11)",
  "rgba(197, 104, 29, 0.07)",
];

const mouse = ref({
  x: undefined,
  y: undefined,
});

class Particle {
  constructor(x, y) {
    this.x = x;
    this.y = y;
    this.size = Math.random() * 5 + 1;
    this.speedX = Math.random() * 3 - 1.5;
    this.speedY = Math.random() * 3 - 1.5;
    this.color = marsColors[Math.floor(Math.random() * marsColors.length)];
  }

  update() {
    this.x += this.speedX;
    this.y += this.speedY;
    if (this.size > 0.2) this.size -= 0.05;
  }

  draw() {
    if (!ctx) return;
    ctx.fillStyle = this.color;
    ctx.beginPath();
    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2);
    ctx.fill();
  }
}

const handleParticles = () => {
  for (let i = particlesArray.value.length - 1; i >= 0; i--) {
    particlesArray.value[i].update();
    particlesArray.value[i].draw();

    if (particlesArray.value[i].size <= 0.3) {
      particlesArray.value.splice(i, 1);
    }
  }
};

const animate = () => {
  if (!ctx || !canvasElement.value) return;

  ctx.clearRect(
    0,
    0,
    canvasElement.value.width,
    canvasElement.value.height
  );
  handleParticles();
  animationFrameId = requestAnimationFrame(animate);
};

const handleCreateParticles = (count, event) => {
  mouse.value.x = event.x;
  mouse.value.y = event.y;
  for (let i = 0; i < count; i++) {
    particlesArray.value.push(new Particle(mouse.value.x, mouse.value.y));
  }
};

const handleWindowResize = () => {
  if (canvasElement.value) {
    canvasElement.value.width = window.innerWidth;
    canvasElement.value.height = window.innerHeight;
  }
};

onMounted(() => {
  if (canvasElement.value) {
    ctx = canvasElement.value.getContext("2d");
    handleWindowResize(); 

    canvasElement.value.addEventListener("click", (e) => handleCreateParticles(15, e));
    canvasElement.value.addEventListener("mousemove", (e) => handleCreateParticles(2, e));
    window.addEventListener("resize", handleWindowResize);

    animate();
  }
});

onBeforeUnmount(() => {
  cancelAnimationFrame(animationFrameId);

  if (canvasElement.value) {
    canvasElement.value.removeEventListener("click", (e) => handleCreateParticles(15, e));
    canvasElement.value.removeEventListener("mousemove", (e) => handleCreateParticles(2, e));
    window.removeEventListener("resize", handleWindowResize);
  }
});
</script>

<style>
#canvas1 {
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  z-index: 2;
  background-color: rgba(0, 0, 0, 0.39);
}
</style>
