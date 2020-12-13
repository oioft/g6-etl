<template>
  <div id="app">
    <G6ETL mode="edit">

    </G6ETL>
  </div>
</template>

<script>
import G6ETL from './components/G6ETL'
export default {
  name: 'app',
  components:{G6ETL}
}
</script>

<style>
html, body {
    overflow: hidden;
    margin: 0;
    font-size: 12px;
}
#app{
  margin: 0;
  padding: 0;
}
</style>
