<script>

export default{
  data(){
    return{

    }
  },
  props: {
    dataListProp: Array
  }
}
</script>

<template>
  <div id="dataTableDiv">
    <table>
      <tr v-for="(value, index) in dataListProp">
        <td>{{index+'  '+value.operator}}</td>
      </tr>
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
  }
</style>