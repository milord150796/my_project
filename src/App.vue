<template>
  <Backgraund/>
  <PageHeader/>
  <MainContent/>
  <CardDonat/>
  <PageFooter/>
</template>

<script>
import PageHeader from './components/PageHeader.vue'
import PageFooter from './components/PageFooter.vue'
import MainContent from './components/MainContent.vue'
import CardDonat from './components/CardDonat.vue'
import Backgraund from './components/Backgraund.vue'



export default {
  name: 'App',
  components: { 
    Backgraund,
    PageHeader,
    PageFooter,
    MainContent,
    CardDonat
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
}
</style>
