<template>
    <router-link class="btn-link" to="/Todolist"> 
      <button class="btn">TODOLIST</button>
    </router-link>
</template>

<style scoped>
  .btn {
    border: none;
    padding:15px;
    background-color:rgb(109, 220, 109);
    border-radius: 4px;
    display: block;  
    max-width: 500px;
    margin: 100px auto;
    cursor: pointer;
  }

  .btn-link {
    text-decoration: none;
    color:#000;
  }
</style>