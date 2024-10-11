<script setup>
import { ref } from 'vue'
import BaseAccordions from './components/BaseAccordions.vue'
import BaseDialog from './components/BaseDialog.vue'
import CustomDialog from './components/CustomDialog.vue'

const dialogVisible = ref(false)

const dialogData = {
  title: '秋天的散步',
  content: '秋天的午後，陽光透過樹葉的縫隙灑下金色的光芒，微風輕拂，帶來一絲涼意。沿著小路散步，地面上鋪滿了五顏六色的落葉，有的如紅酒般濃烈，有的則像陽光下的檸檬，閃耀著明亮的黃色。',
}

const detailList = [{
  title: '秋日的黃昏',
  content: '隨著夏天的腳步漸漸遠去，秋天的黃昏帶來了一絲清新的涼意。樹葉在微風中輕輕搖曳，金黃的色彩如同大自然的調色盤，斑駁而美麗。這個季節總是讓人感到特別的平靜。',
}, {
  title: '夜空的星辰',
  content: '夜幕降臨，天空中繁星閃爍。我坐在院子裡，仰望著無垠的星空，心中感受到一種無法言喻的寧靜。每顆星星都像是遙遠的夢想，閃爍著希望的光芒。此時此刻，煩惱與憂慮都隨著夜風遠去。大自然的壯麗讓我意識到，生活中有太多美好的事物值得我們去珍惜。',
}, {
  title: '書店的秘密',
  content: '在城市的一角，有一家古老的書店，裡面散發著淡淡的書香。每當我踏進這個小小的世界，時間似乎都靜止了。書架上擺滿了各式各樣的書籍，它們靜靜地講述著不同的故事。我喜歡在角落裡的沙發上坐下，隨意翻閱那些封面上泛黃的書本。每一本書都是一個新世界，帶我踏上未知的旅程。',
}, {
  title: '海邊的回憶',
  content: '夏天的海邊，海浪輕輕拍打著岸邊，留下白色的泡沫。陽光灑在沙灘上，金色的光輝讓人感到無比溫暖。我和朋友們一起嬉戲，堆沙堡、撿貝殼，笑聲在空中迴蕩。這些美好的回憶將永遠印在心中，成為青春的印記。海邊的每一個瞬間都是那麼珍貴，像是生命中閃耀的星光。',
}]
</script>

<template>
  <div class="container">
    <CustomDialog />

    <button class="openButton" @click="dialogVisible = true">
      <span>開啟 Dialog</span>
      <span class="material-symbols-outlined openIcon">dialogs</span>
    </button>

    <BaseDialog v-model="dialogVisible" :dialog-data="dialogData">
      <template #close="{ closeHandle }">
        <button @click="closeHandle">
          關掉
        </button>
      </template>
    </BaseDialog>

    <BaseAccordions v-for="(detail, id) in detailList" :key="`Accordion${id}`" :detail-data="detail" />
  </div>
</template>

<style scoped>
.container {
  position: absolute;
  top: 10%;
  left: 20%;
  display: grid;
  grid-template: 100px 1fr / 600px;
  justify-content: flex-start;
  align-content: flex-start;
}

.openButton {
  display: flex;
  justify-content: center;
  align-items: center;
  width: max-content;
  height: max-content;
  padding: 15px 20px;
  color: rgb(250, 250, 250);
  font: 700 32px '';
  background-color: rgb(29, 171, 218);
  border-radius: 5px;
  cursor: pointer;
}

.openButton .openIcon {
  font-size: 36px;
  padding-left: 20px;
}
</style>
