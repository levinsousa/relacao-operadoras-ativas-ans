<script>
  import Header from './components/Header.vue';
  import MainDiv from './components/MainDiv.vue';
  import InsertBox from './components/InsertBox.vue';

  export default{
    data(){
      return{
        operatorList: []
      }
    }
    ,components: {
      Header,
      MainDiv,
      InsertBox
    },
    methods: {
      insertOperator(response){
        this.operatorList.push({
          operator: response.name
        })
      }
    }
  }
</script>

<template>
  <Header />
  <MainDiv v-bind:dataProp="operatorList"/>
  <InsertBox v-on:insert-operator="insertOperator"/>
</template>

<style>
@import './assets/base.css';
</style>
