<template>
    <section class="contact-form-section">
      <h2>Свяжитесь с нами</h2>
      
      <form @submit.prevent="submitForm" class="contact-form">
        <div class="form-group">
          <label for="name">Имя*</label>
          <input 
            type="text" 
            id="name" 
            v-model="form.name" 
            @blur="validateField('name')"
            :class="{ error: errors.name }"
          >
          <span class="error-message" v-if="errors.name">{{ errors.name }}</span>
        </div>
        
        <div class="form-group">
          <label for="email">Email*</label>
          <input 
            type="email" 
            id="email" 
            v-model="form.email" 
            @blur="validateField('email')"
            :class="{ error: errors.email }"
          >
          <span class="error-message" v-if="errors.email">{{ errors.email }}</span>
        </div>
        
        <div class="form-group">
          <label for="phone">Телефон</label>
          <input 
            type="tel" 
            id="phone" 
            v-model="form.phone" 
            @blur="validateField('phone')"
            :class="{ error: errors.phone }"
          >
          <span class="error-message" v-if="errors.phone">{{ errors.phone }}</span>
        </div>
        
        <div class="form-group">
          <label for="message">Сообщение*</label>
          <textarea 
            id="message" 
            v-model="form.message" 
            @blur="validateField('message')"
            :class="{ error: errors.message }"
          ></textarea>
          <span class="error-message" v-if="errors.message">{{ errors.message }}</span>
        </div>
        
        <button type="submit" class="submit-btn">Отправить</button>
      </form>
      
      <Modal 
        v-if="showModal" 
        :success="formSuccess" 
        :message="modalMessage"
        @close="showModal = false"
      />
    </section>
  </template>
  
  <script>
  import Modal from './Modal.vue'
  
  export default {
    name: 'ContactForm',
    components: {
      Modal
    },
    data() {
      return {
        form: {
          name: '',
          email: '',
          phone: '',
          message: ''
        },
        errors: {
          name: '',
          email: '',
          phone: '',
          message: ''
        },
        showModal: false,
        formSuccess: false,
        modalMessage: ''
      }
    },
    methods: {
      validateField(field) {
        if (field === 'name') {
          if (!this.form.name.trim()) {
            this.errors.name = 'Поле обязательно для заполнения'
          } else if (this.form.name.length < 2) {
            this.errors.name = 'Имя должно содержать минимум 2 символа'
          } else {
            this.errors.name = ''
          }
        }
        
        if (field === 'email') {
          const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/
          if (!this.form.email.trim()) {
            this.errors.email = 'Поле обязательно для заполнения'
          } else if (!emailRegex.test(this.form.email)) {
            this.errors.email = 'Введите корректный email'
          } else {
            this.errors.email = ''
          }
        }
        
        if (field === 'phone') {
          const phoneRegex = /^\+?\d{10,15}$/
          if (this.form.phone && !phoneRegex.test(this.form.phone)) {
            this.errors.phone = 'Введите корректный номер телефона'
          } else {
            this.errors.phone = ''
          }
        }
        
        if (field === 'message') {
          if (!this.form.message.trim()) {
            this.errors.message = 'Поле обязательно для заполнения'
          } else if (this.form.message.length < 10) {
            this.errors.message = 'Сообщение должно содержать минимум 10 символов'
          } else {
            this.errors.message = ''
          }
        }
      },
      validateForm() {
        this.validateField('name')
        this.validateField('email')
        this.validateField('phone')
        this.validateField('message')
        
        return !Object.values(this.errors).some(error => error)
      },
      submitForm() {
        if (this.validateForm()) {
          this.formSuccess = true
          this.modalMessage = 'Ваше сообщение успешно отправлено! Мы свяжемся с вами в ближайшее время.'
          this.showModal = true
          
          this.form = {
            name: '',
            email: '',
            phone: '',
            message: ''
          }
        } else {
          this.formSuccess = false
          this.modalMessage = 'Пожалуйста, исправьте ошибки в форме.'
          this.showModal = true
        }
      }
    }
  }
  </script>
  
  <style lang="scss" scoped>
  .contact-form-section {
    max-width: 800px;
    margin: 0 auto;
    padding: 2rem;
  
    h2 {
      font-size: 2rem;
      margin-bottom: 2rem;
      color: #2c3e50;
      text-align: center;
    }
  }
  
  .contact-form {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
    background-color: white;
    padding: 2rem;
    border-radius: 8px;
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
  
    .form-group {
      display: flex;
      flex-direction: column;
      gap: 0.5rem;
  
      label {
        font-weight: 600;
        color: #2c3e50;
      }
  
      input, textarea {
        padding: 0.75rem;
        border: 1px solid #ddd;
        border-radius: 4px;
        font-size: 1rem;
        transition: border-color 0.3s;
  
        &:focus {
          border-color: #42b983;
          outline: none;
        }
  
        &.error {
          border-color: #e74c3c;
        }
      }
  
      textarea {
        min-height: 120px;
        resize: vertical;
      }
  
      .error-message {
        color: #e74c3c;
        font-size: 0.875rem;
      }
    }
  
    .submit-btn {
      background-color: #42b983;
      color: white;
      border: none;
      padding: 0.75rem 1.5rem;
      font-size: 1rem;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s;
      align-self: flex-start;
  
      &:hover {
        background-color: #3aa876;
      }
    }
  }
  
  @media (max-width: 800px) {
    .contact-form-section {
      padding: 1rem;
    }
  }
  
  @media (max-width: 550px) {
    .contact-form {
      padding: 1.5rem;
  
      h2 {
        font-size: 1.5rem;
      }
    }
  }
  </style>