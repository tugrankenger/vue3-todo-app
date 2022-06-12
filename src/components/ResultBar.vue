<template>
    <div class="d-flex justify-content-between px-1">
        <small class="text-success me-2">Completed item count: {{ completed }}</small>
        <small class="text-danger me-2">Uncompleted item count: {{ unCompleted }}</small>
    </div>
</template>

<script>
    export default{
        props: ["completed", "unCompleted"]
    }
</script>