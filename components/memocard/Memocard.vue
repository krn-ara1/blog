<script setup>
const props = defineProps({
  article: {
    type: Object,
    required: true,
  },
});

// 日付をフォーマットする
const date = new Date(props.article.date);
const dateHyphen = date.toLocaleDateString("sv-SE");
const dateSlash = dateHyphen.replaceAll("-", "/");

// 記事が新しいか判定する
const today = new Date();
const millisecondsPerDay = 86400000;
const term = (today - date) / millisecondsPerDay;
const daysRecent = 14;
const isNew = term <= daysRecent;

// 画像の縦横比に従ってレイアウトを変更する
const memocardImage = ref(null);
let isVertical = ref(false);
onMounted(() => {
  const memocardImageOffsetWidth = memocardImage.value.offsetWidth;
  const memocardImageOffsetHeight = memocardImage.value.offsetHeight;
  isVertical.value = memocardImageOffsetWidth <= memocardImageOffsetHeight;
});
</script>

<template>
  <NuxtLink
    class="memocardContainer"
    :class="{ vertical: isVertical }"
    href="#"
  >
    <div class="memocardClip first"></div>
    <div class="memocardHead">
      <time class="memocardDate" :datetime="dateHyphen">{{ dateSlash }}</time>
      <img
        v-show="isNew"
        class="memocardNewpinIcon"
        src="/icon_newpin.png"
        width="132"
        height="132"
        loading="lazy"
        alt="new"
      />
    </div>
    <div class="memocardBody">
      <img
        class="memocardImage"
        :src="props.article.thumb"
        ref="memocardImage"
        loading="lazy"
      />
      <h3 class="memocardTitle">{{ props.article.title }}</h3>
    </div>
    <div class="memocardFoot">
      <span class="memocardText">この記事を読む</span>
    </div>
    <div class="memocardClip second"></div>
  </NuxtLink>
</template>

<style scoped>
.memocardContainer {
  padding: var(--xs);
  border: 1px solid var(--color-text);
  background-color: #fffdc1;
  box-shadow: 4px 4px 4px -4px #808080;
  display: flex;
  flex-direction: column;
  gap: var(--xs);
  position: relative;
  transition: box-shadow  0.2s;
}
.memocardContainer:hover {
  box-shadow: 3px 3px 2px -4px #808080;
}
.memocardHead {
  position: relative;
  display: flex;
  justify-content: flex-end;
}
.memocardDate {
  font-size: 0.5rem;
}
.memocardNewpinIcon {
  z-index: 3;
  width: calc(0.5rem * 4);
  height: auto;
  position: absolute;
  bottom: 100%;
  left: 100%;
  transform: translateX(3px);
}
.memocardBody {
  display: flex;
  flex-direction: column;
  gap: var(--xs);
}
.vertical .memocardBody {
  flex-direction: row;
}
.memocardTitle {
  font-size: 0.8rem;
}
.memocardImage {
  display: block;
  width: 100%;
  height: auto;
  filter: contrast(0.8);
  transition: filter 0.2s linear;
}
.memocardContainer:hover .memocardImage {
  filter: contrast(1);
}
.vertical .memocardImage {
  width: 50%;
}
.memocardFoot {
}
.memocardText {
  font-size: 0.8rem;
  position: relative;
  z-index: 1;
}
.memocardText::before {
  background: linear-gradient(transparent 10%, rgb(255, 130, 96) 50%);
  content: "";
  display: block;
  width: 100%;
  height: 100%;
  position: absolute;
  left: 0;
  bottom: 0;
  margin: auto;
  transform: scale(0, 1);
  transform-origin: left top;
  transition: transform 0.3s ease-out;
  z-index: -1;
}
.memocardContainer:hover .memocardText::before {
  transform-origin: left top;
  transform: scale(1, 1);
}
/* 挟み込み */
/* .memocardClip {
  z-index: 1;
  background-color: var(--color-text);
  height: 40px;
  width: 40px;
  clip-path: polygon(0 0, 100% 0, 0 100%);
  position: absolute;
}
.memocardClip::before {
  z-index: 2;
  content: "";
  box-shadow: none;
  background-color: #fff;
  height: 40px;
  width: 40px;
  clip-path: polygon(0 0, 100% 0, 0 100%);
  position: absolute;
}
.memocardClip.first {
  top: 0;
  left: 0;
  transform: translateX(-10px) translateY(-10px);
}
.memocardClip.first::before {
  top: 0;
  left: 0;
  transform: translateX(-0.5px) translateY(-0.5px);
}
.memocardClip.second {
  bottom: 0;
  right: 0;
  transform: translateX(10px) translateY(10px) rotate(180deg);
}
.memocardClip.second::before {
  bottom: 0;
  right: 0;
  transform: translateX(-0.5px) translateY(-0.5px);
} */
</style>
