<script setup>
const link = ref("www.naver.com");
const props = defineProps(['SelectedProp']);
const { SelectedProp } = toRefs(props);
const SelectedSprite = computed(() => {
    return SelectedProp.value.sprite;
})
const SelectedColor = computed(()=>{
    return SelectedProp.value.color;
})

function ColorCheckF(){
    return 'color' in SelectedProp.value;
}
function temp(){
    console.log(SelectedColor.value)
}
</script>
<template>
    <div class="ObjectTable">
        <div class="ObjectColor ObjectTableItem" v-if="ColorCheckF()">
            <div class="ObjectTableTopic">색상</div>
            <div class="ObjectColorLine LineSize">
                <button class="ImgMargin" @click="SelectedSprite=ImgColor.sprite" v-for="ImgColor in SelectedColor">
                    <img class="LineImg" :src="ImgColor.sprite" />
                </button>
            </div>
        </div>
        <div class="ObjectVector ObjectTableItem">
            <div class="ObjectTableTopic">방향</div>
            <div class="ObjectVectorLine LineSize">
                <button class="ImgMargin" v-for="(i, index) in 4">
                    <img class="LineImg" :style="{ transform: 'rotate(' + (index * 90) + 'deg)' }"
                        :src="SelectedSprite" />
                </button>
            </div>
        </div>
        <div class="ObjectLink ObjectTableItem">
            <div class="ObjectTableTopic">링크</div>
            <div class="ObjectLinkLine">
                <button class="ObjectLinkLineButton">{{ link }}</button>
            </div>
        </div>
        <div class="Accept">
            <button @click="temp()" class="AcceptButton">배치하기</button>
        </div>
    </div>
</template>
<style scoped>
.ObjectTable {
    margin-top: 10%;
}

.ObjectTableItem {
    display: flex;
    margin-bottom: 5%;
}

.ObjectTableTopic {
    width: 25%;
    background-color: white;
    color: #964b00;
    border-style: solid;
    border-color: #964b00;
    border-radius: 30px;
    font-size: x-small;
    margin-left: 5%;
    margin-right: 5%;
}

.LineImg {
    width: 19px;
}

.LineSize {
    width: 60%;
}

.ImgMargin {
    margin-right: 10%;
    background-color: transparent;
}

.AcceptButton {
    background-color: #B58948;
    border-radius: 30px;
    width: 200px;
    height: 40px;
    margin-top: 10px;
}

.ObjectLinkLine {
    background-color: #B58948;
    border-radius: 30px;
    width: 55%;
}

.ObjectLinkLineButton {
    background-color: transparent;
    color: black;
    font-size: small;
    font-weight: lighter;
}
</style>