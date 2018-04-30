<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <img src="https://i0.wp.com/upload.wikimedia.org/wikipedia/en/e/ef/StackExchange_Rubber_Duck_Avatar_April_Fools_2018.png?zoom=2&resize=270%2C270&ssl=1" alt="">
  
    
    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
