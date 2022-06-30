<template>
  <!-- <emit @customChange="logChange" :testEmit="testEmit"></emit> -->
    <listView test="My journey with Vue" :projects="projects" />
</template>

<script>
import listView from './ListView.vue'
// import Emit from './components/EmitComponent.vue'
import {reactive} from 'vue'
export default {
  components: {
    listView,
    // Emit
  },
  setup() {
    let projects = reactive({data: [
      {
        id:1,
        title: 'hello word',
        text: 'hello',
      }, 
      {
        id: 2,
        title: 'bye bye',
        text: 'see you ',
      }, 
      {
        id: 3,
        title: 'hehe',
        text: 'yoyo',
      }
    ]})
    // console.log(projects);
    function logChange(e) {
      console.log(e);
    }
  
    return{projects, logChange}
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
.todo-list {
  margin-bottom: 40px;
  font-size: 40px;
  font-weight: 700;
}
.form {
  display: flex;
  gap: 20px;
  max-width: 500px;
  margin: 0 auto;
}
.form input {
  padding: 5px 15px;
}
.form button {
  border: none;
  background: blueviolet;
  border-radius: 4px;
  cursor: pointer;
}
.list {
  border: 1px solid red;
  margin: 20px auto ;
  padding: 10px 0;
  max-width: 500px;
  background: #42b983;
}
.list button {
  margin: 0 10px;
  background:blueviolet;
  border: none;
  padding: 10px;
  border-radius: 4px;
}
</style>