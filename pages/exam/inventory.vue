<script setup>
import List from "~/components/Inventory/List.vue";
import Detail from "~/components/Inventory/Detail.vue";

const ImgID = ref('');
function temp(ID){
    ImgID.value = ID;
}
</script>

<template>
    <div class="root">
        <List @selected="temp"/>
        <Detail :ImgIDProp= "ImgID"/>
    </div>
</template>

<style scoped>
</style>