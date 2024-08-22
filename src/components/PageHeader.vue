<template>
 <div class="container">
  <div class="game-container">
    <h2>🎮 Mini Game: Click the Box!</h2>
    <div
      v-for="box in boxes"
      :key="box.id"
      :class="['box', { active: box.active }]"
      @click="handleClick(box)"
    >
      <span v-if="box.active">🔥</span>
    </div>
    <p>Score: {{ score }}</p>
    <button @click="startGame">Start Game</button>
  </div>
 </div>
</template>

<script>
export default {
  data() {
    return {
      boxes: [
        { id: 1, active: false },
        { id: 2, active: false },
        { id: 3, active: false },
        { id: 4, active: false },
        { id: 5, active: false },
        { id: 6, active: false },
        { id: 7, active: false },
        { id: 8, active: false },
      ],
      score: 0,
      gameInterval: null,
    };
  },
  methods: {
    startGame() {
      this.score = 0;
      this.resetBoxes();
      clearInterval(this.gameInterval);

      this.gameInterval = setInterval(() => {
        this.activateRandomBox();
      }, 1000);
    },
    resetBoxes() {
      this.boxes.forEach((box) => (box.active = false));
    },
    activateRandomBox() {
      this.resetBoxes();
      const randomIndex = Math.floor(Math.random() * this.boxes.length);
      this.boxes[randomIndex].active = true;
    },
    handleClick(box) {
      if (box.active) {
        this.score++;
        box.active = false;
      }
    },
  },
  beforeUnmount() {
    clearInterval(this.gameInterval);
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

.game-container {
  text-align: center;
  margin-top: 60px;
}

.box {
  width: 100px;
  height: 100px;
  background-color: #f0f0f0;
  display: inline-flex;
  margin: 20px;
  border-radius: 8px;
  cursor: pointer;
  font-size: 2rem;
  align-items: center;
  justify-content: center;
  transition: background-color 0.3s ease;
}

.box.active {
  background-color: #ff6347;
  color: #fff;
}
</style>
