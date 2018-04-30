<template>
  <div class="HelloWorld">
    <div>
      <h1>{{ title }}</h1>
    </div>
    <div>
      <input type="text" v-model="inputTodo" @keyup.enter="addItem">
      <button @click="addItem">Add</button>
    </div>
    <div>
      <ul>
        <li v-for="(item,index) in todoLists" v-bind:class="{finished: item.isFinished}">
          {{item.label}}
          <button v-on:click="toggleFinish(item)">Done</button>
          <button @click="removeItem">Delete</button>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import Storage from './localStorage'

export default {
  name: 'HelloWorld',
  data () {
    return {
      title: 'Todo List',
      todoLists: Storage.fetch(),
      inputTodo: ''
    }
  },
  methods: {
    addItem: function() {
      this.todoLists.push({
        label: this.inputTodo,
        isFinished: false
      })
      this.inputTodo = ''
    },
    toggleFinish: function(item) {
      item.isFinished = !item.isFinished
    },
    removeItem: function(index) {
      this.todoLists.splice(index, 1)
    }
  },
  watch:{
  	todoLists:{
	  	 handler: function (todoLists) {
	      Storage.save(todoLists);//监控li变化，将新增的值存入 localStorage 里
	    },										
	  	deep:true							
  	}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.finished {
  border-radius: 1px solid black;
  background: #42b983;
  
}
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 10px;
  margin-bottom: 10px;
}
a {
  color: #42b983;
}
</style>
