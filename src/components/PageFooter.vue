<template>
  <footer class="site-footer">
    <p>© 2024 Мій Сайт. Всі права захищені.</p>
    <div class="snake-container" @click="scrollToTop">
      <div class="snake">
        <div class="snake-body"></div>
        <div class="snake-body"></div>
        <div class="snake-body"></div>
        <div class="snake-body"></div>
        <div class="snake-head"></div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  methods: {
    scrollToTop() {
      window.scrollTo({
        top: 0,
        behavior: 'smooth',
      });
    },
  },
};
</script>

<style scoped>
.site-footer {
  background-color: #333;
  color: white;
  text-align: center;
  padding: 1rem;
  margin-top: auto;
  position: relative;
}

.snake-container {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 1rem;
  cursor: pointer;
}

.snake {
  position: relative;
  width: 150px;
  height: 20px;
  display: flex;
  align-items: center;
  animation: slither 2s linear infinite;
}

.snake-body,
.snake-head {
  background-color: #4CAF50;
  border-radius: 50%;
}

.snake-body {
  width: 20px;
  height: 20px;
  margin-right: 5px;
}

.snake-head {
  width: 25px;
  height: 25px;
  background-color: #FF6347;
}

@keyframes slither {
  0% {
    transform: translateX(0);
  }
  50% {
    transform: translateX(-10px);
  }
  100% {
    transform: translateX(0);
  }
}
</style>
