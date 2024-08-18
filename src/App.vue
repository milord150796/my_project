<template>
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


export default {
  name: 'App',
  components: { 
    PageHeader,
    PageFooter,
    MainContent,
    CardDonat
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
