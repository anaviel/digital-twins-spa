<template>
    <div class="modal-overlay" @click.self="$emit('close')">
      <div class="modal" :class="{ success: success, error: !success }">
        <button class="close-btn" @click="$emit('close')">&times;</button>
        <div class="modal-content">
          <div class="modal-icon">
            <i v-if="success" class="fas fa-check-circle"></i>
            <i v-else class="fas fa-exclamation-circle"></i>
          </div>
          <h3>{{ success ? 'Успех!' : 'Ошибка' }}</h3>
          <p>{{ message }}</p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'Modal',
    props: {
      success: Boolean,
      message: String
    },
    emits: ['close']
  }
  </script>
  
  <style lang="scss" scoped>
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 1000;
  }
  
  .modal {
    background-color: white;
    border-radius: 8px;
    padding: 2rem;
    max-width: 500px;
    width: 90%;
    position: relative;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15);
  
    &.success {
      border-top: 4px solid #42b983;
    }
  
    &.error {
      border-top: 4px solid #e74c3c;
    }
  }
  
  .close-btn {
    position: absolute;
    top: 10px;
    right: 10px;
    background: none;
    border: none;
    font-size: 1.5rem;
    cursor: pointer;
    color: #666;
    transition: color 0.3s;
  
    &:hover {
      color: #333;
    }
  }
  
  .modal-content {
    text-align: center;
    padding: 1rem;
  
    .modal-icon {
      font-size: 3rem;
      margin-bottom: 1rem;
  
      .fa-check-circle {
        color: #42b983;
      }
  
      .fa-exclamation-circle {
        color: #e74c3c;
      }
    }
  
    h3 {
      font-size: 1.5rem;
      margin-bottom: 1rem;
      color: #2c3e50;
    }
  
    p {
      color: #666;
      line-height: 1.5;
    }
  }
  
  @media (max-width: 550px) {
    .modal {
      padding: 1.5rem;
    }
  }
  </style>