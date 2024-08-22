<template>
  <div class="animated-background">
    <h2>"Ласкаво просимо на наш сайт! У нас навіть Wi-Fi швидший, ніж ваша бабуся з пакунками!"</h2>
    <p>🎉😎 Ласкаво просимо до сторінки з крутим ефектом фону! 😎🎉</p>
  </div>
</template>

<script>
export default {
  name: 'AnimatedBackgroundPage',
};
</script>

<style scoped>
.animated-background {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: white;
  overflow: hidden;
  position: relative;
  background: linear-gradient(120deg, #2980b9, #8e44ad);
}

.animated-background::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.1), transparent 70%);
  animation: animate 10s linear infinite;
}

@keyframes animate {
  0% {
    transform: translate(-50%, -50%) rotate(0deg);
  }
  100% {
    transform: translate(-50%, -50%) rotate(360deg);
  }
}

h2 {
  font-size: 3rem;
  margin-bottom: 1rem;
  z-index: 1;
}

p {
  font-size: 1.5rem;
  z-index: 1;
}
</style>
