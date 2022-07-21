<script setup>
import Data from "~/assets/inventoy";

</script>

<template>
<div class="Inventory">
    <div class="Title">오브젝트 선택</div>
    <div class="InventoryTable">
        <button class="InventoryImg" @click="$emit('selected', i.id)" v-for="i in Data">
            <img class="InventoryImgSprite" :src="i.sprite">
        </button>
    </div>
</div>
</template>
<style scoped>
.Inventory {
    width: 512px;
    padding: 16px;
    text-align: center;
}
.Title {
    margin-bottom: 10px;
    background-color: #FFF6D5;
    border-radius: 30px;
    text-align: center;
}
.InventoryTable {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
}
.InventoryImg {
    width: 70%;
    margin: auto;
    background: none;
}

.InventoryImgSprite{
    width: 100%;
    image-rendering: pixelated;
}
</style>