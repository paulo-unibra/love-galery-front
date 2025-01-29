<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import Carrousel from './components/Carrousel.vue'
import { ref } from 'vue';

const isOpen = ref(false);
const menuItems = ref(['Início', 'Sobre', 'Serviços', 'Contato']);

function toggleMenu() {
  isOpen.value = !isOpen.value;
}

</script>

<template>
  <div id="app" class="d-flex">
    <!-- Sidebar -->
    <!-- <div :class="['sidebar', { 'sidebar-open': isOpen }]">
      <ul class="list-group list-group-flush">
        <li class="list-group-item" v-for="item in menuItems" :key="item">{{ item }}</li>
      </ul>

      <button :class="['hamburger-btn', { 'is-open': isOpen, 'is-close': !isOpen }]" class="m-3" @click="toggleMenu">
        <span></span>
        <span></span>
        <span></span>
      </button>
    </div> -->

    <!-- Main Content -->
    <div class="flex-grow-1">
      <RouterView />
    </div>
  </div>

</template>

<style scoped>
/* Estilo do menu lateral */
.sidebar {
  width: 0;
  overflow: hidden;
  transition: width 0.3s ease;
  background-color: var(--sidebar-bg-color);
  border-right: 1px solid var(--sidebar-border-color);
  position: fixed;
  height: 100vh;
  z-index: 1040;
}

.sidebar-open {
  width: 250px;
}

.flex-grow-1 {
  margin-left: 0;
  transition: margin-left 0.3s ease;
}

.sidebar-open+.flex-grow-1 {
  margin-left: 250px;
}

:root {
  --sidebar-bg-color: #f8f9fa;
  --sidebar-border-color: #dee2e6;
  --text-color: #000;
  --hamburger-color: #000;
}

[data-theme="dark"] {
  --sidebar-bg-color: #343a40;
  --sidebar-border-color: #495057;
  --text-color: #f8f9fa;
  --hamburger-color: #f8f9fa;
}

body {
  color: var(--text-color);
}

/* Estilo do botão hambúrguer */
.hamburger-btn {
  background: none;
  border: none;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  width: 30px;
  height: 30px;
  padding: 0;
  z-index: 1050;
  position: absolute;
  right: 10px;
  top: 10px;
}

.hamburger-btn span {
  display: block;
  width: 100%;
  height: 3px;
  background-color: var(--hamburger-color);
  border-radius: 2px;
  transition: transform 0.3s, opacity 0.3s, background-color 0.3s;
}

.button-toggle {
  padding: 10px;
  position: absolute;
}

.hamburger-btn.is-close {
  /* .hamburger-btn.is-open */
  left: 30px;
  position: fixed;
}

.hamburger-btn.is-open span:nth-child(1) {
  transform: translateY(9px) rotate(45deg);
}

.hamburger-btn.is-open span:nth-child(2) {
  opacity: 0;
}

.hamburger-btn.is-open span:nth-child(3) {
  transform: translateY(-11px) rotate(-45deg);
}
</style>
