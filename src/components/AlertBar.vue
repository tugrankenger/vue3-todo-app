<template>
    <div v-if="alertBar.length < 1" class="alert alert-warning">
        There are no records added yet
    </div>
</template>

<script>
    export default{
        props:["alertBar"]
    }
</script>