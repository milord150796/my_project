<template>
    <div id="app">
        <div class="animation-container">
            <!-- Літак -->
            <svg class="plane" viewBox="0 0 200 100" xmlns="http://www.w3.org/2000/svg">
                <rect x="20" y="40" width="160" height="20" rx="10" fill="#2c3e50" />
                <polygon points="20,50 5,35 5,65" fill="#1f8ecd" />
                <polygon points="180,50 195,35 195,65" fill="#1f8ecd" />
                <circle cx="50" cy="50" r="6" fill="#95a5a6" />
                <circle cx="150" cy="50" r="6" fill="#95a5a6" />
            </svg>

            <!-- Людина з парашутом -->
            <svg class="parachute" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg"
                v-show="parachuteOpened && !hasLanded">
                <ellipse cx="50" cy="30" rx="30" ry="20" fill="url(#parachuteGradient)" />
                <line x1="35" y1="50" x2="30" y2="80" stroke="#34495e" stroke-width="2" />
                <line x1="65" y1="50" x2="70" y2="80" stroke="#34495e" stroke-width="2" />
                <!-- Людина з великою зброєю -->
                <circle cx="50" cy="80" r="8" fill="#ffdab9" />
                <rect x="45" y="90" width="10" height="20" fill="#34495e" />
                <rect x="40" y="95" width="5" height="15" fill="#34495e" />
                <rect x="55" y="95" width="5" height="15" fill="#34495e" />
                <!-- Зброя -->
                <rect x="58" y="90" width="30" height="6" fill="#2c3e50" />
                <rect x="85" y="88" width="10" height="10" fill="#2c3e50" />
            </svg>

            <!-- Пальми -->
            <div class="palm-tree" v-show="hasLanded && !showDonateMessage">
                🌴
            </div>
            <div class="palm-tree" v-show="hasLanded && !showDonateMessage">
                🌴
            </div>

            <!-- Банани -->
            <div class="bananas" v-show="showDonateMessage">
                🍌🍌🍌
            </div>

            <!-- Повідомлення про донат -->
            <div class="donate-message" v-show="showDonateMessage">💰 Підтримайте нас донатом!</div>
        </div>
        <button @click="startAnimation">Почати анімацію</button>
    </div>
</template>

<script>
export default {
    name: 'App',
    data() {
        return {
            parachuteOpened: false,
            hasLanded: false,
            showDonateMessage: false
        };
    },
    methods: {
        startAnimation() {
            this.parachuteOpened = true;
            setTimeout(() => {
                this.hasLanded = true;
            }, 3000);

            setTimeout(() => {
                this.showDonateMessage = true;
            }, 5000);
        }
    }
};
</script>

<style scoped>
.animation-container {
    position: relative;
    height: 100vh;
    overflow: hidden;
    background: linear-gradient(135deg, #2980b9, #2c3e50);
    display: flex;
    justify-content: center;
    align-items: center;
}

.plane {
    position: absolute;
    top: 10%;
    left: 10%;
    width: 200px;
    animation: planeFly 6s linear infinite;
}

.parachute {
    position: absolute;
    top: 50%;
    left: 30%;
    width: 100px;
    animation: parachuteDescend 3s ease-out forwards;
}

.palm-tree {
    position: absolute;
    font-size: 6rem;
    /* Збільшено розмір пальм */
    animation: palmAnimation 2s ease forwards;
    top: 75%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.palm-tree:nth-child(1) {
    animation-delay: 0.3s;
}

.palm-tree:nth-child(2) {
    animation-delay: 0.6s;
    left: 40%;
}

.bananas {
    position: absolute;
    font-size: 3rem;
    top: 60%;
    left: 50%;
    transform: translateX(-50%);
    animation: bananaDrop 2s ease forwards;
}

.donate-message {
    position: absolute;
    bottom: 15%;
    left: 50%;
    transform: translateX(-50%);
    font-size: 2rem;
    color: white;
    padding: 1rem;
    background: rgba(0, 0, 0, 0.7);
    border-radius: 12px;
    text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.5);
    animation: fadeIn 2s ease-out;
}

button {
    margin-top: 20px;
    padding: 10px 20px;
    font-size: 1rem;
    border: none;
    background-color: #3498db;
    color: white;
    cursor: pointer;
    border-radius: 5px;
    transition: background-color 0.3s ease;
    margin-bottom: 20px;
}

button:hover {
    background-color: #2980b9;
}

@keyframes planeFly {
    0% {
        transform: translateX(-100vw);
    }

    100% {
        transform: translateX(100vw);
    }
}

@keyframes parachuteDescend {
    0% {
        top: 10%;
    }

    100% {
        top: 70%;
    }
}

@keyframes palmAnimation {
    0% {
        transform: translate(-50%, -50%) scale(0);
        opacity: 0;
    }

    100% {
        transform: translate(-50%, -50%) scale(1);
        opacity: 1;
    }
}

@keyframes bananaDrop {
    0% {
        opacity: 0;
        transform: translateX(-50%) translateY(-20px);
    }

    100% {
        opacity: 1;
        transform: translateX(-50%) translateY(0);
    }
}

@keyframes fadeIn {
    0% {
        opacity: 0;
    }

    100% {
        opacity: 1;
    }
}
</style>