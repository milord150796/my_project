<template>
    <div>
      <button class="red-button" @click="openModal">{{ buttonText }}</button>
  
      <!-- Модальне вікно -->
      <div v-if="isModalVisible" class="modal-overlay">
        <div class="modal">
          <span class="close-button" @click="closeModal">&times;</span>
          <p>Закинь донатик на каву та отримай її з нашого сайту!</p>
  
          <!-- Форма для введення даних карти -->
          <form @submit.prevent="handleDonation">
            <div class="form-group">
              <label for="card-number">Номер картки (16 цифр):</label>
              <input
                type="text"
                id="card-number"
                v-model="cardNumber"
                @input="formatCardNumber"
                maxlength="19"
                required
                placeholder="1234 5678 9012 3456"
              />
              <p v-if="cardNumberError" class="error">{{ cardNumberError }}</p>
            </div>
            <div class="form-group">
              <label for="expiry-date">Дата випуску (MM/YY):</label>
              <input
                type="text"
                id="expiry-date"
                v-model="expiryDate"
                @input="formatExpiryDate"
                maxlength="5"
                required
                placeholder="MM/YY"
              />
              <p v-if="expiryDateError" class="error">{{ expiryDateError }}</p>
            </div>
            <div class="form-group">
              <label for="cvv">CVV (3 цифри):</label>
              <input
                type="text"
                id="cvv"
                v-model="cvv"
                maxlength="3"
                required
                placeholder="123"
              />
              <p v-if="cvvError" class="error">{{ cvvError }}</p>
            </div>
            <div class="form-group">
              <label for="amount">Сума донату:</label>
              <input
                type="number"
                id="amount"
                v-model="amount"
                required
                min="1"
                placeholder="Введіть суму"
              />
            </div>
            <button type="submit" class="donate-button" :disabled="!isFormValid">
              Зробити донат
            </button>
          </form>
  
          <p>
            <a
              href="http://kavaveterana.intita.com/"
              :class="{ disabled: !donationConfirmed }"
              v-if="donationConfirmed"
            >
              Отримати каву за донат
            </a>
          </p>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'RedCompon',
    data() {
      return {
        buttonText: 'Click Me',
        isModalVisible: false,
        cardNumber: '',
        expiryDate: '',
        cvv: '',
        amount: '',
        donationConfirmed: false,
        cardNumberError: '',
        expiryDateError: '',
        cvvError: '',
      };
    },
    computed: {
      isFormValid() {
        return !this.cardNumberError && !this.expiryDateError && !this.cvvError && this.amount > 0;
      },
    },
    methods: {
      openModal() {
        this.isModalVisible = true;
      },
      closeModal() {
        this.isModalVisible = false;
      },
      formatCardNumber() {
        this.cardNumber = this.cardNumber.replace(/\s+/g, '').replace(/(\d{4})(?=\d)/g, '$1 ').slice(0, 19);
        this.validateCardNumber();
      },
      formatExpiryDate() {
        this.expiryDate = this.expiryDate.replace(/[^0-9]/g, '').replace(/(\d{2})(?=\d)/g, '$1/').slice(0, 5);
        this.validateExpiryDate();
      },
      validateCardNumber() {
        const cardNumberPattern = /^\d{4}\s\d{4}\s\d{4}\s\d{4}$/;
        if (!cardNumberPattern.test(this.cardNumber)) {
          this.cardNumberError = 'Номер картки має містити 16 цифр у форматі "1234 5678 9012 3456".';
        } else {
          this.cardNumberError = '';
        }
      },
      validateExpiryDate() {
        const expiryDatePattern = /^(0[1-9]|1[0-2])\/\d{2}$/;
        if (!expiryDatePattern.test(this.expiryDate)) {
          this.expiryDateError = 'Дата має бути у форматі "MM/YY".';
        } else {
          this.expiryDateError = '';
        }
      },
      validateCVV() {
        const cvvPattern = /^\d{3}$/;
        if (!cvvPattern.test(this.cvv)) {
          this.cvvError = 'CVV має містити 3 цифри.';
        } else {
          this.cvvError = '';
        }
      },
      handleDonation() {
        this.validateCardNumber();
        this.validateExpiryDate();
        this.validateCVV();
  
        if (this.isFormValid) {
          this.donationConfirmed = true;
          alert(`Дякуємо за донат! Картка: ${this.cardNumber}, Сума: ${this.amount} грн`);
        } else {
          alert('Будь ласка, перевірте введені дані.');
        }
      },
    },
  };
  </script>
  
  <style scoped>
  a {
    text-decoration: none;
    color: blue;
    cursor: pointer;
  }
  
  a.disabled {
    pointer-events: none;
    color: grey;
  }
  
  .red-button {
    background-color: #e74c3c;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
    transition: background-color 0.3s ease;
    margin-bottom: 20px;
    }
  
  .red-button:hover {
    background-color: #c0392b;
  }
  
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 3;
  }
  
  /* .modal {
    background-color: white;
    padding: 20px;
    border-radius: 10px;
    text-align: center;
    position: relative;
    width: 400px;
  } */

  .modal {
  background: linear-gradient(135deg, #6a11cb, #2575fc);
  padding: 20px;
  border-radius: 10px;
  text-align: center;
  position: relative;
  width: 400px;
  color: white;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
  animation: gradient-animation 10s ease infinite;
}

/* Анімація для плавного переливання кольорів */
@keyframes gradient-animation {
  0% {
    background: linear-gradient(135deg, #6a11cb, #2575fc);
  }
  33% {
    background: linear-gradient(135deg, #43cea2, #185a9d);
  }
  66% {
    background: linear-gradient(135deg, #ff4e50, #f9d423); /* Без оранжевих відтінків */
  }
  100% {
    background: linear-gradient(135deg, #6a11cb, #2575fc);
  }
}

  
  .close-button {
    position: absolute;
    top: 10px;
    right: 15px;
    font-size: 24px;
    cursor: pointer;
  }
  
  .close-button:hover {
    color: #e74c3c;
  }
  
  .modal p {
    font-size: 18px;
    margin: 10px 0;
  }
  
  .form-group {
    margin-bottom: 15px;
    text-align: left;
  }
  
  .form-group label {
    display: block;
    margin-bottom: 5px;
  }
  
  .form-group input {
    width: 96%;
    padding: 8px;
    border-radius: 5px;
    border: 1px solid #ccc;
  }
  
  .donate-button {
    background-color: #27ae60;
    color: white;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 16px;
  }
  
  .donate-button:disabled {
    background-color: grey;
  }
  
  .donate-button:hover:enabled {
    background-color: #219150;
  }
  
  .error {
    color: red;
    font-size: 14px;
  }
  </style>
  