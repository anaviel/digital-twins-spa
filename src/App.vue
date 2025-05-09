<template>
    <div class="app">
      <Header @change-tab="changeActiveTab" />
      <main>
        <HomeSection v-if="activeTab === 'home'" />
        <TechnologiesSection v-if="activeTab === 'technologies'" />
        <ContactForm v-if="activeTab === 'contact'" />
      </main>
    </div>
  </template>
  
  <script>
  import Header from './components/Header.vue'
  import HomeSection from './components/HomeSection.vue'
  import TechnologiesSection from './components/TechnologiesSection.vue'
  import ContactForm from './components/ContactForm.vue'
  
  export default {
    name: 'App',
    components: {
      Header,
      HomeSection,
      TechnologiesSection,
      ContactForm
    },
    data() {
      return {
        activeTab: 'home'
      }
    },
    methods: {
      changeActiveTab(tab) {
        this.activeTab = tab
      }
    }
  }
  </script>
  
  <style lang="scss">
 @import '@/assets/styles/main.scss';
  
  .app {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
  
  main {
    flex: 1;
    padding: 2rem;
    margin-top: 60px;
  }
  </style>