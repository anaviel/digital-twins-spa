<template>
  <section class="home-section">
    <h1>Цифровые двойники: виртуальные копии реальных объектов</h1>
    
    <div class="content">
      <div class="text-content">
        <p class="intro">
          Цифровой двойник — это динамическая виртуальная копия физического объекта, процесса или системы, 
          которая в реальном времени отражает его состояние через интеграцию с датчиками и аналитическими моделями.
        </p>
        
        <div class="feature-block">
          <h2>Ключевые особенности</h2>
          <div class="feature-table">
            <div class="feature-row">
              <div class="feature-title">Реальная синхронизация</div>
              <div class="feature-desc">Непрерывный обмен данными с физическим объектом</div>
            </div>
            <div class="feature-row">
              <div class="feature-title">Прогностическая аналитика</div>
              <div class="feature-desc">Моделирование различных сценариев развития</div>
            </div>
            <div class="feature-row">
              <div class="feature-title">Глубокая оптимизация</div>
              <div class="feature-desc">Анализ данных для повышения эффективности</div>
            </div>
            <div class="feature-row">
              <div class="feature-title">Технологическая интеграция</div>
              <div class="feature-desc">Совместимость с IoT, AI и Big Data</div>
            </div>
          </div>
        </div>

        <div class="applications-block">
          <h2>Области применения</h2>
          <div class="applications-grid">
            <div class="application-item">
              <div class="application-icon">🏭</div>
              <h3>Промышленность</h3>
              <p>Мониторинг оборудования, прогнозирование поломок, оптимизация процессов. Лидеры: Siemens, GE Digital.</p>
            </div>
            
            <div class="application-item">
              <div class="application-icon">🌆</div>
              <h3>Умные города</h3>
              <p>Моделирование инфраструктуры, управление ресурсами. Сингапур реализовал цифровую копию города.</p>
            </div>
            
            <div class="application-item">
              <div class="application-icon">⚕️</div>
              <h3>Медицина</h3>
              <p>Персонализированные модели пациентов, симуляция лечения. Используется в разработке терапий.</p>
            </div>
            
            <div class="application-item">
              <div class="application-icon">🚘</div>
              <h3>Транспорт</h3>
              <p>Виртуальные испытания, тестирование автономных систем. Tesla применяет для всех моделей.</p>
            </div>
          </div>
        </div>

        <div class="tech-block">
          <h2>Базовые технологии</h2>
          <div class="tech-list">
            <div class="tech-item">
              <h3>3D-моделирование</h3>
              <p>Точные цифровые копии объектов</p>
            </div>
            <div class="tech-item">
              <h3>Интернет вещей</h3>
              <p>Датчики для сбора данных</p>
            </div>
            <div class="tech-item">
              <h3>Искусственный интеллект</h3>
              <p>Анализ и прогнозирование</p>
            </div>
          </div>
        </div>
      </div>
      
      <GallerySlider />
    </div>
  </section>
</template>

<script>
import GallerySlider from './GallerySlider.vue'

export default {
  name: 'HomeSection',
  components: {
    GallerySlider
  }
}
</script>

<style lang="scss" scoped>
.home-section {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;

  h1 {
    font-size: 2.5rem;
    margin-bottom: 1.5rem;
    color: #2c3e50;
    font-weight: 600;
  }

  h2 {
    font-size: 1.8rem;
    margin: 2.5rem 0 1.2rem;
    color: #2c3e50;
    font-weight: 500;
    position: relative;
    padding-bottom: 0.5rem;

    &::after {
      content: '';
      position: absolute;
      bottom: 0;
      left: 0;
      width: 60px;
      height: 3px;
      background: #42b983;
    }
  }

  h3 {
    font-size: 1.3rem;
    margin: 1rem 0 0.5rem;
    color: #2c3e50;
  }

  .content {
    display: flex;
    gap: 3rem;
    margin-top: 1rem;
    align-items: flex-start;

    .text-content {
      flex: 1;
    }
  }

  .intro {
    font-size: 1.1rem;
    line-height: 1.7;
    color: #444;
    margin-bottom: 2rem;
  }

  .feature-block {
    margin: 2rem 0;
  }

  .feature-table {
    display: table;
    width: 100%;
    border-collapse: collapse;
    margin-top: 1rem;
  }

  .feature-row {
    display: table-row;
  }

  .feature-title, .feature-desc {
    display: table-cell;
    padding: 0.8rem 0.5rem;
    vertical-align: top;
    border-bottom: 1px solid #f0f0f0;
  }

  .feature-title {
    width: 35%;
    font-weight: 500;
    color: #2c3e50;
    padding-right: 1rem;
  }

  .feature-desc {
    color: #4a5568;
    line-height: 1.5;
  }

  .feature-row:last-child .feature-title,
  .feature-row:last-child .feature-desc {
    border-bottom: none;
  }

  @media (max-width: 768px) {
    .feature-table, 
    .feature-row,
    .feature-title, 
    .feature-desc {
      display: block;
      width: 100%;
    }
    
    .feature-title {
      padding-bottom: 0.3rem;
      border-bottom: none;
      font-weight: 600;
    }
    
    .feature-desc {
      padding-top: 0;
      padding-bottom: 1rem;
    }
    
    .feature-row {
      margin-bottom: 0.8rem;
      padding-bottom: 0.8rem;
      border-bottom: 1px solid #f0f0f0;
    }
    
    .feature-row:last-child {
      border-bottom: none;
      margin-bottom: 0;
      padding-bottom: 0;
    }
  }

  .applications-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 1.5rem;
    margin: 1.5rem 0;
  }

  .application-item {
    background: white;
    border-radius: 8px;
    padding: 1.5rem;
    box-shadow: 0 2px 12px rgba(0,0,0,0.08);
    transition: transform 0.3s, box-shadow 0.3s;

    &:hover {
      transform: translateY(-3px);
      box-shadow: 0 4px 16px rgba(0,0,0,0.12);
    }
  }

  .application-icon {
    font-size: 1.8rem;
    margin-bottom: 0.8rem;
    opacity: 0.8;
  }

  .tech-list {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 1.2rem;
    margin: 1.2rem 0;
  }

  .tech-item {
    background: #f0f7f4;
    padding: 1.2rem;
    border-radius: 6px;
    text-align: center;
  }

  @media (max-width: 800px) {
    .content {
      flex-direction: column;
      gap: 2rem;
    }

    .applications-grid,
    .tech-list {
      grid-template-columns: 1fr;
    }
  }

  @media (max-width: 550px) {
    padding: 1.2rem;

    h1 {
      font-size: 2rem;
    }

    h2 {
      font-size: 1.5rem;
    }

    .feature-title {
      min-width: 140px;
    }
  }
}
</style>