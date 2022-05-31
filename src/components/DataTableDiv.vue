<script>

export default{
  data(){
    return{

    }
  },
  props: {
    dataListProp: Object
  }
}
</script>

<template>
  <div id="dataTableDiv">
    <table>
      <thead>
        <tr>
          <th v-for="(value) in dataListProp.head">{{value}}</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(prop, index) in dataListProp.body">
          <td v-for="(value) in prop">{{value}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style>
  #dataTableDiv{
    height: 300pt;
    margin: 5pt;
    border: 1px dashed rgba(0, 0, 0, 0.37);
    color: rgba(0, 0, 0, 0.6);
    font-weight: 500;
    overflow: scroll;
  }
  table{
    border-collapse: collapse;
  }
  td,th{
    margin: 0;
    border: 1px solid rgba(0, 0, 0, 0.37);
    text-align: center;
    padding: 0 5pt;
  }
  tr{
    height: 30pt;
  }
</style>