<template>
    <div>
        <button class="btn btn-info" :disabled="disable" @click="event">{{ text }}</button>
    </div>
</template>
<script setup>
    const props = defineProps({
        text:{
            type:String,
            required:true
        },
        disable:{
            type:Boolean,
            default:false
        },
        event:{
            type:Function,
        }
    })
</script>