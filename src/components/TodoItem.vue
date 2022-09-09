<template>
    <div class="py-10" v-if="listTasksTodo.length !== 0">
        <div v-for="(itemList, index) in listTasksTodo" :key="index" class="w-4/5 mx-auto h-16 flex items-center justify-between px-3 rounded-2xl shadow-lg shadow-gray-200 text-lg gap-3">
            <div class="flex flex-row-reverse gap-3">
                <label for="inputExaple">{{ itemList }}</label>
                <input type="checkbox" id="inputExample" :value="itemList" v-model="checkedValues" ref="inputValue">
                {{ checkedValues }}
            </div>  
            <button class="cursor-pinter" @click="deleteTask(index)">
                <svg fill="#654ea3" xmlns="http://www.w3.org/2000/svg"  viewBox="0 0 24 24" width="24px" height="24px"><path d="M 10 2 L 9 3 L 4 3 L 4 5 L 5 5 L 5 20 C 5 20.522222 5.1913289 21.05461 5.5683594 21.431641 C 5.9453899 21.808671 6.4777778 22 7 22 L 17 22 C 17.522222 22 18.05461 21.808671 18.431641 21.431641 C 18.808671 21.05461 19 20.522222 19 20 L 19 5 L 20 5 L 20 3 L 15 3 L 14 2 L 10 2 z M 7 5 L 17 5 L 17 20 L 7 20 L 7 5 z M 9 7 L 9 18 L 11 18 L 11 7 L 9 7 z M 13 7 L 13 18 L 15 18 L 15 7 L 13 7 z"/></svg>
            </button>
        </div>
    </div>
    <div v-else class="text-center mt-5 font-medium text-2xl">
        <p> Create your first todo! </p>
    </div>
</template>

<script >
    export default{
        emits:['delete-task'],
        data(){
            return{
                checkedValues: [],
            }
        },
        watch:{
            checkedValues(){
                let arrayInputs = this.$refs.inputValue;
                console.log(arrayInputs)
                //console.log(arrayInputs.map(item => item.value));
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
            }
        }
    }
</script>

<style >

</style>