<script setup>
const color = ref(['brown','#FFECA8']);
const check = ref(false);

function isclick(){
    check.value = !check.value;
    console.log(check.value)
}
function iscolor() {
    if(check.value){
        return color.value[0];
    }
    else{
        return color.value[1];
    }
}
</script>
<template>
<div>
    <h1>Cat 페이지</h1>
    <button class="button" @click="isclick" :style="{ color : iscolor() }">
    클릭
    </button>
</div>
</template>
<style>
</style>