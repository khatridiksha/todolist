<template>
    <div class="overflow-hidden">
        <Todolist />
    </div>
</template>

<script setup lang="ts">
import Todolist from './todolist.vue';


</script>

<style scoped>
.overflow-hidden{
overflow-x: hidden;
overflow-y: hidden;
padding: 0;
margin: 0;
}
</style>