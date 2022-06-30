<template>
    <div class="nav">
   {{ test }}
  <div class="todo-list">TODO LIST</div>
  <form @submit.prevent="onchangeCreate" class="form">
    <input type="text" placeholder="Text" v-model="dataOptions.titleText">
    <input type="text" placeholder="Massage" v-model="dataOptions.descText">
    <button type="submit">ADD Project</button>
  </form>
 
  <div class="list" v-for="(project, index) in dataProject" :key="project.id">
    <h3>Title: {{ project.title }}</h3>
    <p>Message: {{ project.text }}</p>
    <button @click="onChangeEdit(index)"> Edit Project</button>
    <button @click="onChangeRemove(index)" >Remove Project</button>
  </div>
  </div>
</template>
<script>
import { v4 as uuidv4 } from 'uuid';
import { ref, toRefs, reactive} from "vue";
export default {
  props: [
    "test",
    "projects"
  ],
  setup(props) {
    const dataOptions = reactive({ 
       titleText: '',
       descText: ''
    } 
    )
    
    const editedProject = ref(null)
    const {data: dataProject} = toRefs(props.projects)
    console.log(dataProject.value.length);
    function onchangeCreate() {
      if (dataOptions.titleText.length === 0) return;

      if (editedProject.value === null ) {
       dataProject.value.push(
          {
          id: uuidv4( ),
          title: dataOptions.titleText,
          text: dataOptions.descText,
          }
        )  
      } else {
        dataProject.value[editedProject.value].title = dataOptions.titleText
        dataProject.value[editedProject.value].text = dataOptions.descText
        editedProject.value = null
       } 
      dataOptions.titleText = '';
      dataOptions.descText = '';       
    }

    function onChangeRemove(index) {
      dataProject.value.splice(index, 1);
    }
    
    function onChangeEdit(index) {
     dataOptions.titleText = dataProject.value[index].title
     dataOptions.descText = dataProject.value[index].text
     editedProject.value = index
    }
    return { 
      onchangeCreate, 
      dataOptions,
      onChangeRemove, 
      onChangeEdit,
      editedProject, 
      dataProject,
      }
}
}
</script>

<style scoped>
   .todo-list {
  margin-bottom: 40px;
  font-size: 40px;
  font-weight: 700;
  margin-top: 20px;
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
  padding: 5px 10px;
  border-radius: 4px;
  cursor: pointer;
}
.list {
  border: 1px solid #000;
  margin: 20px auto ;
  padding: 10px 0;
  max-width: 500px;
  border-radius: 6px;
}
.list button {
  padding: 10px;
  cursor: pointer;
}
</style>