<template>
  <div class="container">
    <div class="col-12 d-flex gap-4 justify-content-center">
      <div class="card p-5 col-8 my-5">
        <h3 class="text-center">Todo List App</h3>
          <AddSection :addTodo="state.addTodo"/>
          <TodoList :myData="state.todoList" @removeItem="removeItem"/>
          <ResultBar :completed="completedItemCount" :unCompleted="unCompletedItemCount"/>
          <AlertBar :alertBar="state.todoList" />
      </div>
      <CompletedItem :myDataComp="completed(event)"/>
    </div>
  </div>
</template>


<script setup>
import { ref, computed, reactive } from "vue";
import ResultBar from "./components/ResultBar.vue";
import AddSection from "./components/AddSection.vue";
import TodoList from "./components/TodoList.vue";
import AlertBar from "./components/AlertBar.vue";
import CompletedItem from "./components/CompletedItem.vue";


const state = reactive({
  todoList: [
    { id: 1, name: "tugran kenger", "completed": false },
    { id: 2, name: "juliet burke", "completed": false },
    { id: 3, name: "john locke", "completed": false },
  ],

  addTodo(event) {
    state.todoList.push({
      id: new Date().getTime(),
      name: event,
      completed: false
    });
  },

})

const completed = () => {
  return state.todoList.filter(todo => todo.completed)
}

const completedItemCount = computed(() => {
  return state.todoList.filter((t) => t.completed).length;
});

const unCompletedItemCount = computed(() => {
  return state.todoList.filter((t) => !t.completed).length;
});

const removeItem = (todoItem) => {
  state.todoList = state.todoList.filter(todo => todo !== todoItem);
  return state.todoList;
}

</script>
