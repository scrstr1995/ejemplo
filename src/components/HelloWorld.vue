
<template>
<div class="container">
<button class="btn btn-primary">Hola</button>
  <div class="row">
    <div class="col-lg-2">Puto</div>
        <div class="col-lg-2">perro</div>
  </div>
</div>

</template>

<script>
import 'bootstrap/dist/css/bootstrap.css'


export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
