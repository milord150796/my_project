<template>
  <Backgraund />
  <PageHeader />
  <MainContent />
  <CardDonat />
  <AnimeVideo />
  <FeedbackPage />
  <PageFooter />
</template>

<script>
import PageHeader from './components/PageHeader.vue'
import PageFooter from './components/PageFooter.vue'
import MainContent from './components/MainContent.vue'
import CardDonat from './components/CardDonat.vue'
import Backgraund from './components/Backgraund.vue'
import FeedbackPage from './components/FeedbackPage.vue'
import AnimeVideo from './components/AnimeVideo.vue'

export default {
  name: 'App',
  components: { 
    Backgraund,
    PageHeader,
    PageFooter,
    MainContent,
    CardDonat,
    FeedbackPage,
    AnimeVideo
  }
}
</script>

<style>
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  position: relative;
  width: 100%;
  height: 100vh;
  /* overflow: hidden; */
  background: linear-gradient(120deg, #a1c4fd, #c2e9fb, #a1c4fd);
  background-size: 200% 200%;
  animation: gradientAnimation 12s ease infinite;
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

/* Анімовані елементи - хвилі */
.animated-waves::before,
.animated-waves::after {
  content: '';
  position: absolute;
  width: 250px;
  height: 250px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 50%;
  filter: blur(75px);
  animation: waveMove 15s ease-in-out infinite;
}

.animated-waves::before {
  top: -100px;
  left: -100px;
  animation-duration: 20s;
  animation-direction: alternate;
}

.animated-waves::after {
  bottom: -100px;
  right: -100px;
  animation-duration: 18s;
  animation-direction: alternate-reverse;
}

@keyframes waveMove {
  0% {
    transform: translate(0, 0);
  }
  50% {
    transform: translate(75px, -75px) scale(1.1);
  }
  100% {
    transform: translate(0, 0);
  }
}
</style>
