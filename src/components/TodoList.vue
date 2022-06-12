<template>
    <ul class="list-group">
        <TodoListItem @removeItem ="$emit('removeItem', $event)" v-for="todo in myData" :key="todo.id" :item="todo"/>
    </ul>
</template>

<script>
import TodoListItem from "./TodoListItem.vue";
export default {
    props: ["myData", "removeItem"],
    components: { TodoListItem }
}
</script>