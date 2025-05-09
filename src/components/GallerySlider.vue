<template>
    <div class="gallery-slider">
      <div class="slider-container">
        <button class="slider-btn prev" @click="prevSlide">&lt;</button>
        
        <div class="slide-wrapper">
          <div 
            class="slide" 
            v-for="(image, index) in images" 
            :key="index"
            :class="{ active: currentIndex === index }"
          >
            <img :src="image.src" :alt="image.alt">
            <div class="caption">{{ image.caption }}</div>
          </div>
        </div>
        
        <button class="slider-btn next" @click="nextSlide">&gt;</button>
      </div>
      
      <div class="slider-dots">
        <span 
          v-for="(dot, index) in images" 
          :key="index"
          :class="{ active: currentIndex === index }"
          @click="goToSlide(index)"
        ></span>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'GallerySlider',
    data() {
      return {
        currentIndex: 0,
        images: [
          {
            src: require('../assets/images/twin1.jpg'),
            alt: 'Промышленный цифровой двойник',
            caption: 'Цифровой двойник промышленного оборудования'
          },
          {
            src: require('../assets/images/twin2.jpg'),
            alt: 'Городской цифровой двойник',
            caption: 'Цифровая модель умного города'
          },
          {
            src: require('../assets/images/twin3.jpg'),
            alt: 'Медицинский цифровой двойник',
            caption: 'Симуляция медицинских процессов'
          }
        ]
      }
    },
    methods: {
      nextSlide() {
        this.currentIndex = (this.currentIndex + 1) % this.images.length
      },
      prevSlide() {
        this.currentIndex = (this.currentIndex - 1 + this.images.length) % this.images.length
      },
      goToSlide(index) {
        this.currentIndex = index
      }
    }
  }
  </script>
  
  <style lang="scss" scoped>
  .gallery-slider {
    width: 100%;
    max-width: 600px;
    margin: 0 auto;
    position: relative;
  
    .slider-container {
      display: flex;
      align-items: center;
      position: relative;
      height: 400px;
      overflow: hidden;
      border-radius: 8px;
      box-shadow: 0 4px 8px rgba(0, 0, 0, 0.2);
    }
  
    .slide-wrapper {
      flex: 1;
      height: 100%;
      position: relative;
    }
  
    .slide {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      opacity: 0;
      transition: opacity 0.5s ease-in-out;
  
      &.active {
        opacity: 1;
      }
  
      img {
        width: 100%;
        height: 100%;
        object-fit: cover;
      }
  
      .caption {
        position: absolute;
        bottom: 0;
        left: 0;
        right: 0;
        background-color: rgba(0, 0, 0, 0.7);
        color: white;
        padding: 1rem;
        text-align: center;
      }
    }
  
    .slider-btn {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      background-color: rgba(255, 255, 255, 0.7);
      border: none;
      border-radius: 50%;
      width: 40px;
      height: 40px;
      font-size: 1.5rem;
      cursor: pointer;
      z-index: 10;
      transition: background-color 0.3s;
  
      &:hover {
        background-color: rgba(255, 255, 255, 0.9);
      }
  
      &.prev {
        left: 10px;
      }
  
      &.next {
        right: 10px;
      }
    }
  
    .slider-dots {
      display: flex;
      justify-content: center;
      margin-top: 1rem;
      gap: 0.5rem;
  
      span {
        display: block;
        width: 12px;
        height: 12px;
        border-radius: 50%;
        background-color: #ccc;
        cursor: pointer;
        transition: background-color 0.3s;
  
        &.active {
          background-color: #2c3e50;
        }
  
        &:hover {
          background-color: #888;
        }
      }
    }
  }
  
  @media (max-width: 800px) {
    .gallery-slider {
      .slider-container {
        height: 350px;
      }
    }
  }
  
  @media (max-width: 550px) {
    .gallery-slider {
      .slider-container {
        height: 250px;
      }
  
      .slider-btn {
        width: 30px;
        height: 30px;
        font-size: 1rem;
      }
    }
  }
  </style>