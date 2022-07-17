<script setup>
import CatVue from './Cat.vue';
import FloorVue from './Floor.vue';
import inventoryVue from './inventory.vue';
import ProfileVue from './Profile.vue';
import WallpaperVue from './Wallpaper.vue';

const currenttab = ref(FloorVue);
const equalcheck = ref(currenttab);
const tabs = ref([CatVue, ProfileVue, WallpaperVue, FloorVue, inventoryVue]);
const tabsname = ['고양이','프로필','벽지','바닥','가구'];

function isclick(t){
    if(currenttab.value == t){
        return 'brwon';
    }
    else
    {
        return '#FFECA8';
    }
}
</script>

<template>
    <div class="tabpage">
        <button class="tabbutton" v-for="(tab,index) in tabs" 
        @click="currenttab=tab;" :style="{ backgroundColor : isclick(tab) }">
            {{ tabsname[index] }}
        </button>
        <div class="tabcontent">
            <component :is="currenttab" class="tabcomponent"></component>
        </div>
    </div>
</template>

<style>
@font-face {
    font-family: 'maple';
    src: url('/Maplestory Bold.ttf')
}
.tabcomponent{
    background-color: #FFECA8;
    display: flex;
    border-bottom-left-radius: 30px;
    border-bottom-right-radius: 30px;
    border-top-right-radius:30px;
    width: 800px;
}
.tabpage{
    background-color: yellow;
    font-family:'maple';
}
.tabbutton{
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
    height: 50px;
    width : 100px;
    margin-right:20px;
    color:black;
}
</style>