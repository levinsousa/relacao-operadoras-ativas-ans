<script>
  import Header from './components/Header.vue';
  import MainDiv from './components/MainDiv.vue';
  import InsertBox from './components/InsertBox.vue';

  export default{
    data(){
      return{
        operatorList: {
          head: {
            registro: "Registro ANS",
            cnpj: "CNPJ",
            razaoSocial: "Razão Social",
            nomeFantasia: "Nome Fantasia",
            modalidade: "Modalidade",
            logradouro: "Logradouro",
            numero: "Número",
            complemento: "Complemento",
            bairro: "Bairro",
            cidade: "Cidade",
            uf: "UF",
            cep: "CEP",
            ddd: "DDD",
            telefone: "Telefone",
            fax: "Fax",
            email: "Endereço eletrônico",
            representante: "Representante",
            cargo: "Cargo Representante",
            dataDeRegistro: "Data Registro ANS"
          },
          body: []
        }
      }
    }
    ,components: {
      Header,
      MainDiv,
      InsertBox
    },
    methods: {
      insertOperator(response){
        this.operatorList.body.push(response)
      }
    }
  }
</script>

<template>
  <Header />
  <MainDiv v-bind:dataProp="operatorList"/>
  <InsertBox v-bind:dataListProp="operatorList" v-on:insert-operator="insertOperator"/>
</template>

<style>
@import './assets/base.css';
</style>
