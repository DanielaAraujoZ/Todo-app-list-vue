<template>
  <main class="h-screen flex justify-center items-center">
    <div class="h-4/5 bg-white w-2/6 rounded-2xl relative pt-8">
      <div class="flex justify-center items-center gap-12">
        <button type="button" @click="changePendingTasks" :class="{active: statePendingTasks}">Pending Tasks</button>
        <button type="button" @click="changeCompletedTasks" :class="{active: stateCompletedTasks}">Completed Tasks</button>
      </div>
      <div v-if="statePendingTasks">
        <TodoInputNew @set-value="addNewTask"/>
        <TodoItem :listTasksTodo="listTasksTodo" @delete-task="deleteTask" @completed-tasks="completedTasks"/>
      </div>
      <div v-if="stateCompletedTasks">
        <TodoItemCompleted :listCompletedTasks="listCompletedTasks"/>
      </div>
    </div>
  </main>
</template>

<script>
  import TodoItem from './components/TodoItem.vue';
  import TodoInputNew from './components/TodoInputNew.vue';
  import TodoItemCompleted from './components/TodoItemCompleted.vue';

  export default{
    components:{
    TodoItem,
    TodoInputNew,
    TodoItemCompleted
},
    data(){
      return{
        listTasksTodo: [],
        listCompletedTasks: [],
        stateCompletedTasks: false,
        statePendingTasks: true
      }
    },
    methods:{
      addNewTask(taskItem){
        this.listTasksTodo.push({
          task: taskItem,
          completed: false
        });
      },
      deleteTask(index){
        this.listTasksTodo.splice(index,1);
      },
      completedTasks(tasks){
        console.log(tasks);
        this.listCompletedTasks = tasks
      },
      changePendingTasks(){
        this.stateCompletedTasks = false
        this.statePendingTasks = true
      },
      changeCompletedTasks(){
        this.stateCompletedTasks = true
        this.statePendingTasks = false
      }
    }
  }
  
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap');
  html{
    font-family: 'Poppins', sans-serif;
  }
  .active{
    font-weight: 600;
    color: #654ea3;
  }
  .info-text{
    color: #654ea3;
  }
</style>
