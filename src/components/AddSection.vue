<template>
    <div class="d-flex justify-content-center">
          <input type="text" class="form-control my-3" v-model="todoText" @keydown.enter="addTodo(todoText)">
        </div>
</template>

<script>
    export default{
        props:["addTodo"],

        data(){
            return{
                todoText: null
            }
        }
    }
</script>