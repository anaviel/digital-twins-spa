<template>
    <header class="header">
      <nav class="navbar">
        <div class="logo">Digital Twins</div>
        <ul class="nav-links">
          <li :class="{ active: activeTab === 'home' }">
            <a href="#" @click.prevent="changeTab('home')">Главная</a>
          </li>
          <li :class="{ active: activeTab === 'technologies' }">
            <a href="#" @click.prevent="changeTab('technologies')">Технологии</a>
          </li>
          <li :class="{ active: activeTab === 'contact' }">
            <a href="#" @click.prevent="changeTab('contact')">Контакты</a>
          </li>
        </ul>
        <button class="mobile-menu-btn" @click="toggleMobileMenu">
          <span></span>
          <span></span>
          <span></span>
        </button>
      </nav>
    </header>
  </template>
  
  <script>
  export default {
    name: 'Header',
    emits: ['change-tab'],
    data() {
      return {
        activeTab: 'home',
        isMobileMenuOpen: false
      }
    },
    methods: {
      changeTab(tab) {
        this.activeTab = tab
        this.$emit('change-tab', tab)
        this.isMobileMenuOpen = false
      },
      toggleMobileMenu() {
        this.isMobileMenuOpen = !this.isMobileMenuOpen
      }
    }
  }
  </script>
  
  <style lang="scss" scoped>
  .header {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    background-color: #2c3e50;
    color: white;
    z-index: 1000;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  }
  
  .navbar {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 1rem 2rem;
    max-width: 1200px;
    margin: 0 auto;
  }
  
  .logo {
    font-size: 1.5rem;
    font-weight: bold;
  }
  
  .nav-links {
    display: flex;
    list-style: none;
    gap: 2rem;
  
    li {
      a {
        color: white;
        text-decoration: none;
        transition: color 0.3s;
        padding: 0.5rem 1rem;
        border-radius: 4px;
  
        &:hover {
          color: #42b983;
        }
      }
  
      &.active a {
        color: #42b983;
        background-color: rgba(255, 255, 255, 0.1);
      }
    }
  }
  
  .mobile-menu-btn {
    display: none;
    background: none;
    border: none;
    color: white;
    font-size: 1.5rem;
    cursor: pointer;
    flex-direction: column;
    justify-content: space-between;
    height: 24px;
    width: 30px;
  
    span {
      display: block;
      width: 100%;
      height: 3px;
      background-color: white;
      transition: all 0.3s;
    }
  }
  
  @media (max-width: 800px) {
    .nav-links {
      position: fixed;
      top: 60px;
      left: 0;
      right: 0;
      background-color: #2c3e50;
      flex-direction: column;
      align-items: center;
      padding: 1rem 0;
      gap: 1rem;
      clip-path: circle(0px at 90% -10%);
      transition: clip-path 0.5s ease-in-out;
  
      &.open {
        clip-path: circle(1000px at 90% -10%);
      }
    }
  
    .mobile-menu-btn {
      display: flex;
    }
  }
  
  @media (max-width: 550px) {
    .navbar {
      padding: 1rem;
    }
  }
  </style>