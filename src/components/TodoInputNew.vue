<template>
    <div class="w-4/5 mx-auto mt-8 h-12 flex items-center gap-4">
        <input type="text" name="" id="" class="h-full w-9/12 px-4 border rounded-xl focus:outline-none focus:ring-violet-500 focus:ring-1" v-model="taskItem">
        <button type="button" class="h-full bg-violet-400 text-white w-3/12 rounded-xl" @click="setValue"> Add Task </button>
    </div>
</template>

<script>
    export default{
        emits:['set-value'],
        data(){
            return{
                taskItem: ''
            }
        },
        computed:{
            setValue(){
                this.$emit(
                    'set-value',
                    this.taskItem
                );
                this.taskItem = ''
            }
        }
    }

</script>

<style >

</style>