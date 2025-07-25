<template>
  <div class="age-category">
    <h1 class="title">Определение возрастной категории</h1>

    <div class="input-section">
      <label for="age-input" class="input-label">Введите ваш возраст:</label>
      <input
          id="age-input"
          type="number"
          v-model.number="age"
          min="0"
          placeholder="0"
          class="age-input"
          @keyup.enter="determineCategory"
      >
      <button @click="determineCategory" class="submit-btn">Определить</button>
    </div>

    <div v-if="result" class="result-section">
      <p class="result-text">Вы: <strong>{{ result }}</strong></p>
    </div>

    <div v-if="error" class="error-section">
      <p class="error-text">{{ error }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      age: null,
      result: '',
      error: ''
    };
  },
  methods: {
    determineCategory() {
      this.result = '';
      this.error = '';

      if (this.age === null || this.age === '') {
        this.error = 'Пожалуйста, введите возраст';
        return;
      }

      if (this.age < 0) {
        this.error = 'Возраст не может быть отрицательным';
        return;
      }

      if (this.age >= 0 && this.age < 3) {
        this.result = 'Младенец';
      } else if (this.age >= 3 && this.age < 12) {
        this.result = 'Ребенок';
      } else if (this.age >= 12 && this.age < 18) {
        this.result = 'Подросток';
      } else if (this.age >= 18 && this.age < 60) {
        this.result = 'Взрослый';
      } else if (this.age >= 60 && this.age < 120) {
          this.result = 'Пенсионер';
      } else {
        this.result = 'Вечный';
      }
    }
  }
};
</script>

<style scoped>
.age-category {
  background-color: #000000;
  border-radius: 15px;
  box-shadow: 0 5px 25px rgba(0, 0, 0, 0.1);
  padding: 30px;
}

.title {
  color: #ffffff;
  text-align: center;
  margin-bottom: 25px;
  font-size: 1.8rem;
}

.input-section {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.input-label {
  font-weight: 600;
  font-size: 1.1rem;
  color: #ffffff;
}

.age-input {
  padding: 14px;
  font-size: 1.1rem;
  border: 2px solid #e0e7ff;
  border-radius: 10px;
  transition: all 0.3s ease;
}

.age-input:focus {
  border-color: #4d6bff;
  outline: none;
  box-shadow: 0 0 0 3px rgba(77, 107, 255, 0.2);
}

.submit-btn {
  padding: 14px;
  background: linear-gradient(to right, #4d6bff, #8a5cff);
  color: white;
  border: none;
  border-radius: 10px;
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  margin-top: 10px;
}

.submit-btn:hover {
  background: linear-gradient(to right, #3a5af5, #7a4cf5);
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(77, 107, 255, 0.3);
}

.submit-btn:active {
  transform: translateY(0);
}

.result-section {
  background: linear-gradient(to right, #e8f5e9, #d1f7e3);
  border-radius: 10px;
  padding: 20px;
  margin-top: 25px;
  animation: fadeIn 0.5s ease;
}

.result-text {
  font-size: 1.2rem;
  color: #2e7d32;
  text-align: center;
  margin: 0;
}

.error-section {
  background: linear-gradient(to right, #ffebee, #ffdde1);
  border-radius: 10px;
  padding: 20px;
  margin-top: 25px;
  animation: fadeIn 0.5s ease;
}

.error-text {
  font-size: 1.1rem;
  color: #c62828;
  text-align: center;
  margin: 0;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>