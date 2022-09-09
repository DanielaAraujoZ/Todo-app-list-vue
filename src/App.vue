<template>
  <main class="h-screen flex justify-center items-center">
    <div class="h-4/5 bg-white w-2/6 rounded-2xl relative pt-8">
      <TodoInputNew @set-value="addNewTask"/>
      <TodoItem :listTasksTodo="listTasksTodo" @delete-task="deleteTask"/>
    </div>
  </main>
</template>

<script>
  import TodoItem from './components/TodoItem.vue';
  import TodoInputNew from './components/TodoInputNew.vue';

  export default{
    components:{
      TodoItem, TodoInputNew
    },
    data(){
      return{
        listTasksTodo: []
      }
    },
    methods:{
      addNewTask(taskItem){
        this.listTasksTodo.push(taskItem);
      },
      deleteTask(index){
        this.listTasksTodo.splice(index,1);
      }
    }
  }
  
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap');
  html{
    font-family: 'Poppins', sans-serif;
  }
</style>
