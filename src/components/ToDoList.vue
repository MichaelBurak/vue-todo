<template>
  <h1>ToDos</h1>
  <div v-for="todo in list" :key="todo.id" class="list">
    {{ todo.content }}
  </div>
</template>

<script>
export default {
  name: 'ToDoList',
  data() { 
      return {
          list: [{
              id: null,
              title: ""
          }]
    }
      },
      mounted(){
          fetch("http://127.0.0.1:8000/")
          .then(res => res.json())
          .then(data => this.list = data)
          .catch(err => console.log(err))
      }  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
/* just a bit of brutalism  */
@font-face {
  font-family: IBMPlexMono-Light;
  src: url("../assets/IBM_Plex_Mono/IBMPlexMono-Light.ttf");
}

div {
  font-family: IBMPlexMono-Light;
}

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
