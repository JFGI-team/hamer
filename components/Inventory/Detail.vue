<script setup>
import Data from "~/assets/inventoy";
import ObjectTable from "~/components/Detail/ObjectTableItem.vue";
const props = defineProps(['ImgIDProp']);
const { ImgIDProp } = toRefs(props);
const SelectedItem = computed(() => {
    return Data.find(element => element.id === ImgIDProp.value);
});
</script>
<template>
  <div class="ObjectState">
    <div class="Title">오브젝트 상세</div>
    <div class="ObjectStateGroup" v-if="SelectedItem">
      <div class="ObjectTop">
        <div class="ObjectImage">
          <img class="img" :src="SelectedItem.sprite" />
        </div>
        <div class="ObjectName">
          <h1>{{ SelectedItem.name }}</h1>
        </div>
        <ObjectTable :SelectedProp="SelectedItem"/>
      </div>
    </div>
  </div>
</template>
<style scoped>
.Title {
    margin-bottom: 10px;
    background-color: #FFF6D5;
    border-radius: 30px;
    text-align: center;
}

.ObjectState {
    width: 258px;
    padding: 16px;
}

.img {
    margin: 0 auto;
    width:60%;
    image-rendering: pixelated;
}

.ObjectName {
    font-size: larger;
    color: white;
    text-shadow: -1px 0px #964b00, 0px 1px #964b00, 1px 0px #964b00, 0px -1px #964b00;
}

.ObjectTop {
    margin-bottom: 10%;
}

.ObjectStateGroup {
    background-color: #FFF6D5;
    border-radius: 30px;
    height: 95%;
    text-align: center;
}
</style>