<script>
  export default{
    data(){
      return{
        operatorName: ''
      }
    },
    methods: {
      toggleInsertOverlay(){
        const overlay = document.getElementById('insertBox')
        overlay.classList.toggle('setVisible')
      },
      insertOperator(){
        if(this.operatorName.trim() == '') return
        this.$emit('insert-operator', {
          name: this.operatorName
        })
        this.toggleInsertOverlay()
        this.operatorName = ''
      }
    }
  }
</script>

<template>
  <form id="insertBox">
    <button id="quitButton" v-on:click.prevent="toggleInsertOverlay">X</button>
    <input type="text" class="inputText" v-model="operatorName" placeholder="Nome da Operadora...">
    <input type="submit" id="submitButton" value="Inserir" v-on:click.prevent="insertOperator">
  </form>
</template>

<style>
  #insertBox{
    position: absolute;
    padding: 10pt;
    width: 60vw;
    height: 80vh;
    top: 70pt;
    left: 20vw;
    border-radius: 4px;
    background-color: #FFFFFF;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.3);
    visibility: hidden;
  }

  #insertBox.setVisible{
    visibility: visible;
  }

  #quitButton{
    position: absolute;
    top: 2pt;
    right: 2pt;
  }

  input{
    font-size: 14pt;
    padding: 4pt 8pt;
    border: 1px solid rgba(0, 0, 0, 0.3);
    border-radius: 4px;
    margin-bottom: 10pt;
  }

  .inputText{
    width: 80%;
    display: flex;
    flex-direction: column;
  }

  #submitButton{
    color: #FFFFFF;
    background-color: rgb(99, 99, 231);
  }
</style>