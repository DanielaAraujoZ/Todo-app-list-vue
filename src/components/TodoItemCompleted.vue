<template>
    <p class="text-center text-xl my-6 info-text" v-if="listCompletedTasks.length < 1">No tasks completed!</p>
    <div v-for="(itemList, index) in listCompletedTasks" :key="index" class="w-4/5 mx-auto mt-8 h-20 flex items-center border-2 border-purple-400 justify-between px-3 rounded-2xl shadow-lg shadow-gray-200 text-lg gap-3">
        <p class="flex flex-row-reverse gap-3 text-xl">{{ itemList.task }}</p>  
        <p class="text-xs mt-10 bg-green-400 px-4 py-1 rounded-xl text-white"> Completed </p>
    </div>
</template>

<script>
    export default{
        props:{
            listCompletedTasks: Array
        }
    }
</script>