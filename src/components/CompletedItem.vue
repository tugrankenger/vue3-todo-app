<template>
    <div class="card p-5 col-4 my-5">
        <h3>Completed Items:</h3>
    <ul class="list-group my-3">
        <li v-for="todo in myDataComp" class="list-group-item">
            <span v-if="todo.completed == true" class="text-decoration-line-through">{{ todo.name }}</span>
        </li>
    </ul>
    </div>
</template>

<script>
export default {
    props: ["myDataComp"]
}
</script>