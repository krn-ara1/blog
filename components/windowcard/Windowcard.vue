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
const daysRecent = 14
const isNew = term <= daysRecent;
</script>

<template>
  <article class="windowcardContainer">
    <div class="windowcardHead">
      <div class="windowcardDateAndTitle">
        <time class="windowcardDate" :datetime="dateHyphen">{{ dateDot }}</time>
        <h3 class="windowcardTitle">{{ props.article.title }}</h3>
      </div>
      <img v-show="isNew"
        class="windowcardNewflagIcon"
        src="/icon_newflag.png"
        width="137"
        height="64"
        alt="new"
      />
    </div>
    <div class="windowcardBody">
      <img class="windowcardImage" :src="props.article.thumb" />
    </div>
    <div class="windowcardFoot">
      <NuxtLink class="windowcardLink" href="#"
        >この記事の続きを読む<img
          class="windowcardLinkIcon"
          src="/icon_arrow_02.png"
          width="48"
          height="49"
      /></NuxtLink>
      <button class="windowcardButton favorite">
        <img src="/icon_favorite.png" />
      </button>
      <button class="windowcardButton share">
        <img src="/icon_share.png" />
      </button>
    </div>
  </article>
</template>

<style scoped>
.windowcardContainer {
  border-radius: calc(0.8rem * 1);
  padding: var(--xs);
  border: 1px solid var(--color-text);
  background-color: #fefcf0;;
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
}
.windowcardImage {
  border: 1px solid var(--color-text);
  display: block;
  width: 100%;
  height: auto;
}
.windowcardFoot {
  display: flex;
  align-items: center;
  justify-content: flex-end;
}
.windowcardLink {
  font-size: 0.5rem;
  margin-right: auto;
  display: flex;
  gap: calc(0.5rem * 0.5);
}
.windowcardLink:hover{
  animation: zoom .3s;
}
@keyframes zoom {
	50% {
		transform: scale(1.05);
	}
}
/* .windowcardLink {
  font-size: 0.5rem;
  margin-right: auto;
  display: flex;
  gap: calc(0.5rem * 0.5);
  position: relative;
  z-index: 1;
}
.windowcardLink::before {
  background: linear-gradient(transparent 10%, #ff8260cc 50%);
  content: "";
  display: block;
  width: 100%;
  height: 100%;
  position: absolute;
  left: 0;
  bottom: 0;
  margin: auto;
  transform: scale(0, 1);
  transform-origin: right top;
  transition: transform 0.3s;
  z-index: -1;
}
.windowcardLink:hover::before {
  transform-origin: left top;
  transform: scale(1, 1);
} */
.windowcardLinkIcon {
  width: 0.5rem;
  height: auto;
}
.windowcardButton {
  background: inherit;
  border: none;
}
.windowcardButton + .windowcardButton {
  margin-left: calc(0.8rem * 0.25);
}
.windowcardButton img {
  width: 0.8rem;
  height: auto;
}
.windowcardButton.favorite {
}
.windowcardButton.share {
}
</style>
