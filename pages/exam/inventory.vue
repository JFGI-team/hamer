<script>
const link = "www.naver.com"
</script>

<template>
    <div class="root">
        <div class="Inventory">
            <div class="Title">오브젝트 선택</div>
            <div class="InventoryTable">
                <div class="InventoryImg" v-for="i in 16">
                    <img src="/apple.png">
                </div>
            </div>
        </div>
        <div class="ObjectState">
            <div class="Title">오브젝트 상세</div>
            <div class="ObjectStateGroup">
                <div class="ObjectTop">
                    <div class="ObjectImage">
                        <img class="img" src="/apple.png">
                    </div>
                    <div class="ObjectName">
                        <h1>{오브젝트 이름}</h1>
                    </div>
                </div>
                <div class="ObjectTable">
                    <div class="ObjectColor ObjectTableItem">
                        <div class="ObjectTableTopic">색상</div>
                        <div class="ObjectColorLine LineSize">
                            <button class="ImgMargin" v-for="i in 4"><img class="LineImg" src="/apple.png"></button>
                        </div>
                    </div>
                    <div class="ObjectVector ObjectTableItem">
                        <div class="ObjectTableTopic">방향</div>
                        <div class="ObjectVectorLine LineSize">
                            <button class="ImgMargin" v-for="i in 4"><img class="LineImg" src="/apple.png"></button>
                        </div>
                    </div>
                    <div class="ObjectLink ObjectTableItem">
                        <div class="ObjectTableTopic">링크</div>
                        <div class="ObjectLinkLine">
                            <button class="ObjectLinkLineButton">www.naver.com</button>
                        </div>
                    </div>
                    <div class="Accept">
                        <button class="AcceptButton">배치하기</button>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<style scoped>
@font-face {
    font-family: 'maple';
    src: url('/Maplestory Bold.ttf')
}

.root {
    background-color: #FFECA8;
    display: flex;
    border-radius: 30px;
    width: 800px;
    font-family: 'maple';
}

.Inventory {
    width: 512px;
    padding: 16px;
    text-align: center;
}

.InventoryImg {
    width: 70%;
    margin: auto;
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

.ObjectState {
    width: 258px;
    padding: 16px;
}

.img {
    margin: 0 auto;
}

.ObjectName {
    font-size: larger;
    color: white;
    text-shadow: -1px 0px #964b00, 0px 1px #964b00, 1px 0px #964b00, 0px -1px #964b00;
}

.ObjectTop {
    margin-bottom: 20%;
}

.ObjectStateGroup {
    background-color: #FFF6D5;
    border-radius: 30px;
    height: 95%;
    text-align: center;
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
.ObjectLinkLine{
    background-color: #B58948;
    border-radius: 30px;
    width: 55%;
}
.ObjectLinkLineButton{
    background-color: transparent;
    color:black;
    font-size:small;
    font-weight: lighter;
}
</style>