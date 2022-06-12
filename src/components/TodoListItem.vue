<template>
    <li class="list-group-item d-flex justify-content-between align-items-center">
            <div>
                <input class="form-check-input" type="checkbox" v-model="item.completed"
                    :id="`check_dynamic${item.id}`">
                <label class="form-check-label ms-2" :for="`check_dynamic${item.id}`">{{ item.name }}</label>
            </div>
            <button class="btn btn-danger btn-sm" @click="$emit('removeItem',item)">Remove</button>
        </li>
</template>

<script>
    export default{
        props: ["item"]
    }
</script>