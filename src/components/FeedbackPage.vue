<template>
  <div class="container">
    <div class="feedback-container">
        <h2>📝 Залиште свій відгук</h2>
        <form @submit.prevent="submitFeedback">
            <textarea v-model="newFeedback" placeholder="Введіть ваш відгук тут..." required></textarea>
            <button type="submit">Залишити відгук</button>
        </form>

        <div v-if="feedback" class="feedback-display">
            <h3>Ваш відгук:</h3>
            <p>{{ feedback }}</p>
        </div>
    </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            newFeedback: '',
            feedback: '',
        };
    },
    mounted() {
        // Завантаження збереженого відгуку з localStorage при завантаженні сторінки
        const savedFeedback = localStorage.getItem('userFeedback');
        if (savedFeedback) {
            this.feedback = savedFeedback;
        }
    },
    methods: {
        submitFeedback() {
            // Збереження відгуку в localStorage
            this.feedback = this.newFeedback;
            localStorage.setItem('userFeedback', this.newFeedback);
            this.newFeedback = '';
        },
    },
};
</script>

<style scoped>
.container {
  background: linear-gradient(270deg, #ff6b6b, #f0e68c, #66b2ff, #8a2be2);
  background-size: 800% 800%;
  animation: gradientAnimation 8s ease infinite;
  padding: 5% 10%  ;
}

@keyframes gradientAnimation {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}


.feedback-container {
    max-width: 600px;
    margin: 0 auto;
    text-align: center;
}

textarea {
    width: 100%;
    height: 100px;
    margin: 10px 0;
    padding: 10px;
    border-radius: 5px;
    border: 1px solid #ccc;
}

button {
    padding: 10px 20px;
    border: none;
    background-color: #28a745;
    color: white;
    font-size: 1rem;
    cursor: pointer;
    border-radius: 5px;
}

button:hover {
    background-color: #218838;
}

.feedback-display {
    margin-top: 20px;
    background-color: #f0f0f0;
    padding: 15px;
    border-radius: 8px;
}
</style>