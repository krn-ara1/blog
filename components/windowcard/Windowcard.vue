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
const dateDot = dateHyphen.replaceAll("-", ".");
// 記事が新しいか判定する
const today = new Date();
const millisecondsPerDay = 86400000;
const term = (today - date) / millisecondsPerDay;
const daysRecent = 14;
const isNew = term <= daysRecent;
</script>

<template>
  <NuxtLink class="windowcardContainer" href="#">
    <div class="windowcardHead">
      <div class="windowcardDateAndTitle">
        <time class="windowcardDate" :datetime="dateHyphen">{{ dateDot }}</time>
        <h3 class="windowcardTitle">{{ props.article.title }}</h3>
      </div>
      <img
        v-show="isNew"
        class="windowcardNewflagIcon"
        src="/icon_newflag.png"
        width="137"
        height="64"
        loading="lazy"
        alt="new"
      />
    </div>
    <div class="windowcardBody">
      <span class="windowcardText">この記事を読む</span>
      <img class="windowcardImage" :src="props.article.thumb" loading="lazy" />
    </div>
    <div class="windowcardFoot">
      <img
        class="windowcardAction favorite"
        src="/icon_favorite.png"
        loading="lazy"
      />
      <img
        class="windowcardAction share"
        src="/icon_share.png"
        loading="lazy"
      />
    </div>
  </NuxtLink>
</template>

<style scoped>
.windowcardContainer {
  border-radius: calc(0.8rem * 1);
  padding: var(--xs);
  border: 1px solid var(--color-text);
  background-color: #fefcf0;
  box-shadow: 4px 4px 4px -4px #808080;
  display: flex;
  flex-direction: column;
  gap: var(--xs);
}
.windowcardHead {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  border-bottom: 1px solid var(--color-text);
  gap: 0.8rem;
}
.windowcardDateAndTitle {
  display: flex;
  flex-direction: column;
}
.windowcardDate {
  font-size: 0.5rem;
}
.windowcardTitle {
  font-size: 0.8rem;
}
.windowcardNewflagIcon {
  width: calc(0.5rem * 3);
  height: auto;
}
.windowcardBody {
  position: relative;
}
.windowcardText {
  z-index: 20;
  font-size: 0.8rem;
  color: #fff;
  opacity: 0;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
  transition: opacity 0.2s linear;
}
.windowcardContainer:hover .windowcardText,
.windowcardContainer:focus .windowcardText {
  opacity: 1;
}
.windowcardImage {
  z-index: 10;
  border: 1px solid var(--color-text);
  display: block;
  width: 100%;
  height: auto;
  transition: filter 0.2s linear;
}
.windowcardContainer:hover .windowcardImage,
.windowcardContainer:focus .windowcardImage {
  filter: brightness(0.8);
}
.windowcardFoot {
  display: flex;
  align-items: center;
  justify-content: flex-end;
}
.windowcardLinkIcon {
  width: 0.5rem;
  height: auto;
}
.windowcardAction {
  width: 0.8rem;
  height: auto;
}
.windowcardAction + .windowcardAction {
  margin-left: calc(0.8rem * 0.25);
}
.windowcardAction.favorite {
}
.windowcardAction.share {
}
</style>
