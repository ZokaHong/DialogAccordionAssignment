<script setup>
import Accordions from './components/Accordions.vue';
import OpenButton from './components/OpenButton.vue';
import CloseButton from './components/CloseButton.vue';
import Dialog from './components/Dialog.vue'


import { ref } from 'vue';

const isDialogVisible = ref(false)

const openDialog = () => {
  isDialogVisible.value = true
}
const closeDialog = () => {
  isDialogVisible.value = false
}

const dialogItem = ref({
  title: '在小鎮的午後',
  content: '在一個寧靜的小鎮上，午後的陽光柔和地灑在街道上。樹影斑駁，微風輕拂，帶來了遠處花香的氣息。小鎮的生活彷彿在這樣的時光中變得緩慢而恬靜。我坐在咖啡館的戶外座位上，手中捧著一杯剛沖好的拿鐵，熱氣緩緩上升，彷彿在與午後的陽光對話。咖啡館裡傳來輕柔的音樂，伴隨著周圍人們的低語聲，讓人感到一種難以言喻的安逸。不遠處，一位老奶奶正在市場上擺攤，手中拿著新鮮的水果和自家種的蔬菜。她的臉上洋溢著微笑，與路過的每一個人打著招呼。小孩們則在街道上追逐嬉鬧，他們的笑聲如同清脆的鈴聲，回蕩在空氣中。這樣的午後，不僅僅是時間的流逝，更是一種生活的享受。我放下咖啡杯，靜靜地看著眼前的一切，心中充滿了對生活的感激。每一個細微的瞬間，都彷彿在告訴我：生活的美好，常常藏在那些不經意的時刻裡。就在這時，一位年輕的畫家走進了我的視線，她手裡拿著畫板，似乎要將眼前的景象捕捉下來。她專注的神情讓我想起了創作的熱情，無論是畫畫、寫作還是其他形式的表達，都是對生活的熱愛。'
})

const detailItems = ref([
  {
    title: '秋日的黃昏',
    content: '隨著夏天的腳步漸漸遠去，秋天的黃昏帶來了一絲清新的涼意。樹葉在微風中輕輕搖曳，金黃的色彩如同大自然的調色盤，斑駁而美麗。這個季節總是讓人感到特別的平靜。'
  },
  {
    title: '夜空的星辰',
    content: '夜幕降臨，天空中繁星閃爍。我坐在院子裡，仰望著無垠的星空，心中感受到一種無法言喻的寧靜。每顆星星都像是遙遠的夢想，閃爍著希望的光芒。此時此刻，煩惱與憂慮都隨著夜風遠去。大自然的壯麗讓我意識到，生活中有太多美好的事物值得我們去珍惜。'
  },
  {
    title: '書店的秘密',
    content: '在城市的一角，有一家古老的書店，裡面散發著淡淡的書香。每當我踏進這個小小的世界，時間似乎都靜止了。書架上擺滿了各式各樣的書籍，它們靜靜地講述著不同的故事。我喜歡在角落裡的沙發上坐下，隨意翻閱那些封面上泛黃的書本。每一本書都是一個新世界，帶我踏上未知的旅程。'
  },
  {
    title: '海邊的回憶',
    content: '夏天的海邊，海浪輕輕拍打著岸邊，留下白色的泡沫。陽光灑在沙灘上，金色的光輝讓人感到無比溫暖。我和朋友們一起嬉戲，堆沙堡、撿貝殼，笑聲在空中迴蕩。這些美好的回憶將永遠印在心中，成為青春的印記。海邊的每一個瞬間都是那麼珍貴，像是生命中閃耀的星光。'
  },
])

</script>

<template>
  <div class="container">
    <OpenButton @open="openDialog" openButton="openButton">
      <span>開啟 Dialog</span>
      <span class="material-symbols-outlined openIcon">dialogs</span>
    </OpenButton>
    <Dialog :visible="isDialogVisible" @click.self="closeDialog">
      <template #title>
        <h1 class="titleText">{{ dialogItem.title }}</h1>
      </template>
      <template #close>
        <CloseButton @close="closeDialog">
          <span class="material-symbols-outlined closeIcon">
            close
          </span>
        </CloseButton>
      </template>
      <template #content>
        <p class="contentText">{{ dialogItem.content }}</p>
      </template>
    </Dialog>



    <Accordions v-for="item in detailItems">
      <template #title>
        <span class="summaryText">{{ item.title }}</span>
      </template>
      <template #content>
        <p class="detailText">{{ item.content }}</p>
      </template>
    </Accordions>
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
  color: rgb(250, 250, 250);
  font: 700 32px '';
}

.openButton .openIcon {
  font-size: 36px;
  padding-left: 20px;
}

.closeIcon {
  font: 700 45px 'Material Symbols Outlined';
  color: brown;
  cursor: pointer;
}

.summaryText {
  color: rgb(65, 46, 28);
  font: 600 28px '';
}

.detailText {
  color: rgb(57, 28, 28);
  padding: 25px 20px;
  border-top: 1px dotted #000;
  margin: 0;
}

.titleText {
  color: chocolate;
}

.contentText {
  padding: 15px 5px 15px 10px;
  margin: 0 15px;
  border-top: 1px dotted #000;
  font: 400 20px '';
  color: rgb(57, 28, 28);
  grid-area: 2/1/span 1/span 2;
}
</style>
