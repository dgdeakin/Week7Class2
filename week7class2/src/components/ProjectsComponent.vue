<template>
    <div>

        This is from projects component!

        <br>
        Title: {{ title }}
        <br>
        Id: {{ id }}
        <br>
        Description: 
        <p>{{ body }}</p>
        <!-- 1st STEP: Use $emit -->
        <button @click="$emit('increase-size')">Increase Font</button>
        
        <!-- SLOTs STEP 1: Create a new button -->
        <button>Button without SLOT</button>
        <button><slot></slot></button>

    <!-- Named SLOT example -->
        <footer>
            <slot name="footer">
            </slot>
        </footer>


    </div>

</template>

<script setup>

// creating props
const props = defineProps({
    title: String,
    id: Number,
    body: String
})

</script>

<style scoped>

</style>