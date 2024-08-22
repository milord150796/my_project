<template>
    <div class="game-container">
        <div class="game-screen">
            <div v-if="!gameStarted" class="start-screen">
                <button class="button-click" @click="startGame">Почати гру </button>
            </div>
            <div v-if="gameStarted" class="game-elements">
                <div class="basket" :style="{ left: basketX + 'px' }"></div>
                <div v-for="(cup, index) in cups" :key="index" class="cup"
                    :style="{ top: cup.y + 'px', left: cup.x + 'px' }"></div>
                <div v-if="gameOver" class="game-over">
                    <p>Гра закінчена!</p>
                    <p>Ваш результат: {{ score }}</p>
                    <button @click="resetGame">Спробувати знову</button>
                </div>
            </div>
        </div>
        <p v-if="gameStarted && !gameOver">Рахунок: {{ score }}</p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            gameStarted: false,
            gameOver: false,
            basketX: 200,
            cups: [],
            score: 0,
            cupInterval: null,
            cupSpeed: 5,
            cupSpawnRate: 2000, // в мілісекундах
        };
    },
    methods: {
        startGame() {
            this.gameStarted = true;
            this.gameOver = false;
            this.score = 0;
            this.cups = [];
            this.basketX = 200;

            this.cupInterval = setInterval(() => {
                this.spawnCup();
            }, this.cupSpawnRate);

            document.addEventListener('mousemove', this.moveBasket);
            document.addEventListener('keydown', this.moveBasketKeyboard);
            this.gameLoop();
        },
        moveBasket(event) {
            this.basketX = event.clientX - 50; // центрируємо кошик по курсору
        },
        moveBasketKeyboard(event) {
            if (event.key === 'ArrowLeft') {
                this.basketX -= 20;
            } else if (event.key === 'ArrowRight') {
                this.basketX += 20;
            }
        },
        spawnCup() {
            const x = Math.random() * (window.innerWidth - 50);
            this.cups.push({ x, y: 0 });
        },
        gameLoop() {
            const loop = () => {
                if (this.gameStarted && !this.gameOver) {
                    this.cups = this.cups.map(cup => {
                        cup.y += this.cupSpeed;
                        if (cup.y > window.innerHeight - 70 && this.isCupInBasket(cup)) {
                            this.score += 10;
                            return null;
                        }
                        return cup;
                    }).filter(cup => cup !== null);

                    if (this.cups.some(cup => cup.y > window.innerHeight)) {
                        this.gameOver = true;
                        clearInterval(this.cupInterval);
                        document.removeEventListener('mousemove', this.moveBasket);
                        document.removeEventListener('keydown', this.moveBasketKeyboard);
                    }

                    requestAnimationFrame(loop);
                }
            };
            loop();
        },
        isCupInBasket(cup) {
            return cup.x < this.basketX + 100 && cup.x + 50 > this.basketX;
        },
        resetGame() {
            this.startGame();
        },
    },
};
</script>

<style scoped>
.game-container {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: hidden;
  background: linear-gradient(
    rgba(255, 223, 186, 0.8), /* Світлий, прозорий відтінок */
    rgba(255, 105, 97, 0.8)    /* Яскравий, прозорий відтінок */
  );
  text-align: center;
}

.game-screen {
    position: relative;
}

.start-screen {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
}

.game-elements {
    position: relative;
    height: 100vh;
}

.basket {
    position: absolute;
    bottom: 10px;
    width: 100px;
    height: 30px;
    background-color: #4CAF50;
    border-radius: 5px;
    opacity: 4;
}

.cup {
    position: absolute;
    width: 50px;
    height: 50px;
    background-color: #fa4300;
    border-radius: 50%;
}

.game-over {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: rgba(0, 0, 0, 0.8);
    color: white;
    padding: 20px;
    border-radius: 10px;
}
.button-click{
    background-color: springgreen;
    padding: 10px;
    border-radius: 20px;
}
</style>