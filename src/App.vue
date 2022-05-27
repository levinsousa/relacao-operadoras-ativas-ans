<script>
  import Header from './components/Header.vue';
  import MainDiv from './components/MainDiv.vue';

  export default{
    components: {
      Header, MainDiv
    }
  }
</script>

<template>
  <Header></Header>
  <MainDiv></MainDiv>
</template>

<style>
@import './assets/base.css';
</style>
