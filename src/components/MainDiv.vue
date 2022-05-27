<script>
import DataTableDiv from './DataTableDiv.vue';
export default{
    data(){
      return{
      }
    },
    props: {
      dataProp: Array
    },
    methods: {
      toggleInsertOverlay(){
        const overlay = document.getElementById('insertBox')
        overlay.classList.toggle('setVisible')
      }
    }
    ,components: {
      DataTableDiv
    }
  }
</script>

<template>
  <div id="divMain">
    <header>
      <span>Relação de Operadoras Ativas ANS</span>
      <input type="search" name="" id="searchBox">
    </header>
    <DataTableDiv v-bind:dataListProp="dataProp"/>
    <div id="footer">
      <button v-on:click.prevent="toggleInsertOverlay">Inserir</button>
      <button disabled="true">Editar</button>
      <button id="deleteButton" disabled="true">Deletar</button>
    </div>
  </div>
</template>

<style>
  #divMain{
    max-width: 100%;
    border-radius: 4px;
    margin: 20pt;
    padding: 5pt;
    background-color: #FFFFFF;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.05);
  }

  #divMain header{
    max-width: 100%;
    margin: 5pt;
    font-size: 14pt;
    color: #5161F1;
    font-weight: 500;
    display: flex;
    justify-content: space-between;
  }

  #footer{
    max-width: 100%;
    margin: 5pt;
    display: flex;
    justify-content: flex-end;
  }

  button{
    margin-left: 10px;
    padding: 4px 8px;
    font-size: 12pt;
    font-weight: 500;
    text-align: center;
    border: 1px solid rgba(0, 0, 0, 0.37);
    border-radius: 4px;
    background-color: #FFFFFF;
  }

  #deleteButton:disabled{
    color: #ffffff8e;
    background-color: #c47f7f;
  }

  #deleteButton{
    color: #FFFFFF;
    background-color: #e22f2f;
  }
</style>