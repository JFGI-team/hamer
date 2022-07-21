<script setup>
import CatVue from "./Cat.vue";
import FloorVue from "./Floor.vue";
import inventoryVue from "./inventory.vue";
import ProfileVue from "./Profile.vue";
import WallpaperVue from "./Wallpaper.vue";

const TabsComponentTable = {
  Cat : {
    component : CatVue,
    Title : "고양이"
  },
  Floor : {
    component : FloorVue,
    Title : "바닥"
  },
  Inventory : {
    component : inventoryVue,
    Title : "가구"
  },
  Profile : {
    component : ProfileVue,
    Title : "프로필"
  },
  Wallpaper : {
    component : WallpaperVue,
    Title : "벽지"
  }
}

const currenttab = ref("Inventory");
</script>

<template>
  <div class="tabpage">
    <button
      v-for="(tab, key) in TabsComponentTable"
      class="tabbutton"
      :class="{ selected: currenttab === key }"
      @click="currenttab = key">
      {{ tab.Title }}
    </button>
    <div class="tabcontent">
      <component :is="TabsComponentTable[currenttab].component" class="tabcomponent"></component>
    </div>
  </div>
</template>

<style>
@font-face {
  font-family: "maple";
  src: url("/Maplestory Bold.ttf");
}
.tabcomponent {
  background-color: #ffeca8;
  display: flex;
  border-bottom-left-radius: 30px;
  border-bottom-right-radius: 30px;
  border-top-right-radius: 30px;
  width: 800px;
}
.tabpage {
  background-color: yellow;
  font-family: "maple";
}
.tabbutton {
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
  height: 50px;
  width: 100px;
  margin-right: 20px;
  color: black;
  background-color : #ffeca8;
}
.selected {
  background-color: blue;
}
</style>
