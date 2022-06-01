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
        console.log(response)
        this.operatorList.body.push([
          response.registro || 'Não informado',
          response.cnpj || 'Não informado',
          response.razaoSocial || 'Não informado',
          response.nomeFantasia || 'Não informado',
          response.modalidade || 'Não informado',
          response.logradouro || 'Não informado',
          response.numero || 'Não informado',
          response.complemento || 'Não informado',
          response.bairro || 'Não informado',
          response.cidade || 'Não informado',
          response.uf || 'Não informado',
          response.cep || 'Não informado',
          response.ddd || 'Não informado',
          response.telefone || 'Não informado',
          response.fax || 'Não informado',
          response.email || 'Não informado',
          response.representante || 'Não informado',
          response.cargo || 'Não informado',
          response.dataDeRegistro || 'Não informado'
        ])
        console.log(this.operatorList.body)

      }
    }
  }

  try {
    const target = `../Relatorio_cadop.csv`;
    
    const res = await fetch(target, {
      method: 'get',
      headers: {
        'content-type': 'text/csv;charset=UTF-8',
      }
    });

    if (res.status === 200) {
      // Recebe o CSV e converte para String
      const data = await res.text();
      // Converte a String para Array separando por quebra de linha e remove item vazio
      const dataFiltered = data.split(/\r?\n/).filter(x => x.trim().length > 0)
      // Recebe a primeira linha como título da tabela por padrão
      const dataListTitle = dataFiltered[0]
      // Recebe a segunda linha como cabeçario da tabela por padrão e converte 
      // em um novo Array separando por ponto e virgula
      const dataListHead = dataFiltered[1].split(';')
      // Remove o título e cabeçario deixando somente o conteúdo da tabela
      dataFiltered.shift()
      dataFiltered.shift()
      // Remove as aspas extras
      const dataListBody = dataFiltered.map(x => {
        return x.replace(/"/g, '').split(';')
      })
      console.log(dataListBody);

    } else {
      console.log(`Error code ${res.status}`);
    }
  } catch (err) {
    console.log(err)
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
