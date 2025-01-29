<template>
    <div class="carousel">
      <h2>{{ title }}</h2>
      <div class="carousel-container" ref="carouselContainer">
        <div class="carousel-item" v-for="(item, index) in items" :key="index">
          <img :src="item.image" :alt="item.title" />
        </div>
      </div>
      <button class="carousel-button prev" @click="scrollCarousel(-1)">&#10094;</button>
      <button class="carousel-button next" @click="scrollCarousel(1)">&#10095;</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      title: {
        type: String,
        required: true,
      },
      items: {
        type: Array,
        required: true,
      },
    },
    methods: {
      scrollCarousel(direction) {
        const container = this.$refs.carouselContainer;
        const scrollAmount = container.clientWidth * 0.8; // Rola 80% da largura do contêiner
        container.scrollBy({
          left: direction * scrollAmount,
          behavior: 'smooth',
        });
      },
    },
  };
  </script>
  
  <style scoped>
  .carousel {
    position: relative;
    max-width: 1200px;
    margin: 20px auto;
    padding: 20px;
  }
  
  .carousel h2 {
    margin-bottom: 10px;
    color: white;
  }
  
  .carousel-container {
    display: flex;
    overflow-x: auto;
    scroll-behavior: smooth;
    gap: 10px;
    padding: 10px 0;
    scrollbar-width: none; /* Esconde a barra no Firefox */
    -ms-overflow-style: none; /* Esconde a barra no IE/Edge */
  }
  
  .carousel-container::-webkit-scrollbar {
    display: none; /* Esconde a barra no Chrome, Safari e Opera */
  }
  
  .carousel-item {
    flex: 0 0 auto;
    width: 200px;
    transition: transform 0.2s;
  }
  
  .carousel-item img {
    width: 100%;
    border-radius: 8px;
  }
  
  .carousel-button {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    background-color: rgba(0, 0, 0, 0.5);
    border: none;
    color: white;
    font-size: 24px;
    cursor: pointer;
    padding: 10px;
    z-index: 10;
  }
  
  .carousel-button.prev {
    left: 10px;
  }
  
  .carousel-button.next {
    right: 10px;
  }
  
  .carousel-button:hover {
    background-color: rgba(0, 0, 0, 0.8);
  }
  </style>