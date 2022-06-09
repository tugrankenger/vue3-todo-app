<template>
  <div class="container">
    <div class="col-12 d-flex justify-content-center">
      <div class="col-8 my-5">
        <h3 class="text-center">Todo List App</h3>
        <div class="d-flex justify-content-center">
          <input type="text" class="form-control my-3" @keydown.enter="state.addTodo">
        </div>
        <div v-if="state.todoList.length > 0">
          <ul class="list-group">
            <li v-for="todo in state.todoList" key="todo.id"
              class="list-group-item d-flex justify-content-between align-items-center">
              <div>
                <input class="form-check-input" type="checkbox" v-model="todo.completed"
                  :id="`check_dynamic${todo.id}`">
                <label class="form-check-label ms-2" :for="`check_dynamic${todo.id}`">{{ todo.name }}</label>
              </div>
              <button class="btn btn-danger btn-sm" @click="removeItem(todo)">Remove</button>
            </li>
          </ul>
          <div class="d-flex justify-content-between px-1">
            <small class="text-success me-2">Completed item count: {{ completedItemCount }}</small>
            <small class="text-danger me-2">Uncompleted item count: {{ unCompletedItemCount }}</small>
          </div>
          <h3 class="my-3">Completed Items:</h3>
          <ul class="list-group my-3">
            <li v-for="todo in state.todoList" class="list-group">
              <span v-if="todo.completed == true" class="text-decoration-line-through">{{ todo.name }}</span>
            </li>
          </ul>
        </div>
        <div v-else class="alert alert-warning">
          There are no records added yet
        </div>
      </div>
      <div class="col-4">
        {{ state.todoList }}
      </div>
    </div>
  </div>
</template>


<script setup>
import { ref, computed, reactive } from "vue"

const state = reactive({
  todoList: [
    { id: 1, name: "tugran kenger", "completed": false },
    { id: 2, name: "juliet burke", "completed": false },
    { id: 3, name: "john locke", "completed": false },
  ],

  addTodo(event) {
    state.todoList.push({
      id: new Date().getTime(),
      name: event.target.value,
      completed: false
    });
  },

})

const completedItemCount = computed(() => {
  return state.todoList.filter((t) => t.completed).length;
});

const unCompletedItemCount = computed(() => {
  return state.todoList.filter((t) => !t.completed).length;
});

const removeItem = computed((todoItem) => {
  state.todoList = state.todoList.filter(todo => todo !== todoItem);
  return state.todoList;
})

</script>
