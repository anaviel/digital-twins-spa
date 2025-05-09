<template>
    <section class="technologies-section">
      <h2>Технологии цифровых двойников</h2>
      
      <div class="tech-grid">
        <div class="tech-card" v-for="tech in technologies" :key="tech.id">
          <div class="tech-icon">
            <i :class="tech.icon"></i>
          </div>
          <h3>{{ tech.title }}</h3>
          <p>{{ tech.description }}</p>
        </div>
      </div>
      
      <div class="benefits">
        <h3>Преимущества цифровых двойников:</h3>
        <ul>
          <li v-for="(benefit, index) in benefits" :key="index">{{ benefit }}</li>
        </ul>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: 'TechnologiesSection',
    data() {
      return {
        technologies: [
          {
            id: 1,
            title: 'ИИ и машинное обучение',
            icon: 'fas fa-brain',
            description: 'Анализ данных и прогнозирование поведения объектов'
          },
          {
            id: 2,
            title: 'IoT и сенсоры',
            icon: 'fas fa-satellite-dish',
            description: 'Сбор данных в реальном времени с физических объектов'
          },
          {
            id: 3,
            title: '3D моделирование',
            icon: 'fas fa-cube',
            description: 'Создание точных виртуальных копий объектов'
          },
          {
            id: 4,
            title: 'Большие данные',
            icon: 'fas fa-database',
            description: 'Обработка и анализ огромных объемов информации'
          }
        ],
        benefits: [
          'Снижение затрат на разработку и тестирование',
          'Оптимизация процессов и повышение эффективности',
          'Прогнозирование отказов и профилактика проблем',
          'Удаленный мониторинг и управление',
          'Быстрое прототипирование и итерации'
        ]
      }
    }
  }
  </script>
  
  <style lang="scss" scoped>
  .technologies-section {
    max-width: 1200px;
    margin: 0 auto;
    padding: 2rem;
  
    h2 {
      font-size: 2rem;
      margin-bottom: 2rem;
      color: #2c3e50;
      text-align: center;
    }
  
    .tech-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 2rem;
      margin-bottom: 3rem;
    }
  
    .tech-card {
      background-color: white;
      border-radius: 8px;
      padding: 1.5rem;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      transition: transform 0.3s, box-shadow 0.3s;
  
      &:hover {
        transform: translateY(-5px);
        box-shadow: 0 6px 12px rgba(0, 0, 0, 0.15);
      }
  
      .tech-icon {
        font-size: 2rem;
        color: #42b983;
        margin-bottom: 1rem;
      }
  
      h3 {
        font-size: 1.25rem;
        margin-bottom: 0.75rem;
        color: #2c3e50;
      }
  
      p {
        color: #666;
        line-height: 1.5;
      }
    }
  
    .benefits {
      background-color: #f8f9fa;
      padding: 2rem;
      border-radius: 8px;
  
      h3 {
        font-size: 1.5rem;
        margin-bottom: 1rem;
        color: #2c3e50;
      }
  
      ul {
        list-style-type: none;
        padding-left: 0;
  
        li {
          position: relative;
          padding-left: 1.5rem;
          margin-bottom: 0.5rem;
          line-height: 1.6;
  
          &::before {
            content: '✓';
            position: absolute;
            left: 0;
            color: #42b983;
            font-weight: bold;
          }
        }
      }
    }
  }
  
  @media (max-width: 800px) {
    .technologies-section {
      padding: 1rem;
  
      .tech-grid {
        grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
        gap: 1rem;
      }
    }
  }
  
  @media (max-width: 550px) {
    .technologies-section {
      h2 {
        font-size: 1.5rem;
      }
  
      .tech-grid {
        grid-template-columns: 1fr;
      }
    }
  }
  </style>