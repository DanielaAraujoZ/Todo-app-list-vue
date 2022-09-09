<template>
    <div class="py-10" v-if="listTasksTodo.length !== 0">
        <div v-for="(itemList, index) in listTasksTodo" :key="index" class="w-4/5 mx-auto h-20 flex items-center justify-between px-3 rounded-2xl shadow-lg shadow-gray-200 text-lg gap-3">
            <div class="flex flex-row-reverse h-full items-center gap-5">
                <label :class="{completedTask: itemList.completed}">{{ itemList.task }}</label>
                <button type="button" class="w-7 h-6" @click="completedTask(index)" :disabled="itemList.completed">
                    <svg class="w-full" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0" y="0"  viewBox="0, 0, 590.088, 522.431">
                        <g id="layer1">
                            <path :class="{completed: itemList.completed}" d="M3.179,332.702 L0,331.316 C58.162,299.934 102.129,272.143 165.059,241.357 C196.247,287.963 216.275,322.209 244.491,380.721 C317.446,243.823 400.046,84.169 579.494,-0 C573.704,75.61 572.435,133.976 590.088,199.231 C450.006,268.799 337.296,390.748 256.067,520.027 L254.581,522.431 C179.674,436.203 104.663,377.515 3.179,332.702 z" id="path880"/>
                        </g>
                    </svg>
                </button>
            </div> 
            <button :class="{completedDelete: itemList.completed}" @click="deleteTask(index)" :disabled="itemList.completed">
                <img src="../assets/iconDelete.svg" alt="icon-delete">
            </button>
        </div>
    </div>
    <div v-else class="text-center mt-5 font-medium text-xl">
        <p class="info-text"> Create your first todo! </p>
    </div>
</template>

<script >
import { list } from 'postcss'

    export default{
        emits:['delete-task', 'completed-tasks'],
        data(){
            return{
                completedTasks: [],
            }
        },
        props:{
            listTasksTodo: Array
        },
        methods:{
            deleteTask(index){
                this.$emit(
                    'delete-task',
                    index
                )
            },
            completedTask(index){
                this.listTasksTodo[index].completed = true;
                this.completedTasks = this.listTasksTodo.filter((item) => item.completed == true);
                this.$emit(
                    'completed-tasks',
                    this.completedTasks
                )
            }
        }
    }
</script>

<style scoped>
    button svg g path {
        fill: #e9cfe7
    }
    button svg g path:hover{
        fill: #4ade80
    }
    .completed{
        fill: #4ade80
    }
    .completedTask{
        text-decoration: line-through;
        color: #a6a6a7;
        font-weight: 600;
    }
    .completedDelete{
        visibility: hidden;
    }

</style>