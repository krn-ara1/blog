<script setup>
import WindowcardWindowcard from "@/components/windowcard/Windowcard.vue";
import BubbleTrip from "@/assets/svg/bubble_03.svg";

import { pickupTrips } from "~/data/data";

// 領域に入ってきたら表示する
import { useIntersectionObserver } from "~/composables/useIntersectionObserver";
const trip = ref(null);
const triplist = ref(null);
const elements = [
  // trip,
  triplist,
];
onMounted(() => {
  useIntersectionObserver().doObserve(elements);
});
</script>

<template>
  <div class="homeContainer">
    <!-- 旅行セクション -->
    <section id="trip" class="homeSection trip -once" ref="trip">
      <div class="homeSectionWrapper">
        <hgroup class="homeSectionHead">
          <BubbleTrip
            class="homeSectionHeadBackground"
            preserveAspectRatio="none"
          />
          <h2 class="homeSectionTitle">旅行</h2>
          <span class="homeSectionTitleEn">trip</span>
        </hgroup>
        <div class="homeSectionBody">
          <ul class="windowcardsContainer -once" ref="triplist">
            <li
              class="windowcardsItem"
              v-for="(pickupTrip, index) in pickupTrips"
              :key="index"
            >
              <WindowcardWindowcard :article="pickupTrip" />
            </li>
          </ul>
        </div>
        <div class="homeSectionFoot">
          <NuxtLink class="homeSectionLink" href="#"
            >旅行の記事をすべて見る<img
              class="homeSectionLinkIcon"
              src="/icon_arrow_02.png"
              width="48"
              height="49"
              loading="lazy"
          /></NuxtLink>
        </div>
      </div>
    </section>
  </div>
</template>

<style scoped>
.homeContainer {
  padding: var(--m) 0;
  display: flex;
  flex-direction: column;
  gap: var(--m);
}
.homeSection {
  padding: var(--m) 0;
}
.homeSectionWrapper {
  width: 80%;
  max-width: 1024px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: var(--s);
}
.homeSectionHead {
  display: flex;
  align-items: baseline;
  gap: 0.5rem;
  position: relative;
  padding: var(--xs);
}
.homeSectionHeadBackground {
  position: absolute;
  top: calc(var(--xs) * -0.5);
  left: calc(var(--xs) * -1);
  height: 100%;
}
.trip .homeSectionHeadBackground {
  width: calc(var(--xs) * 2 + 0.5rem + 1.4rem * 2 + 1rem * 4);
}
.homeSectionTitle {
  z-index: 2;
  font-size: 1.4rem;
}
.homeSectionTitleEn {
  z-index: 2;
  font-size: 1rem;
  text-transform: uppercase;
}
.homeSectionBody {
}
.windowcardsContainer {
  display: flex;
  gap: var(--s);
  flex-wrap: wrap;
}
.windowcardsItem {
  width: calc(calc(100% - calc(var(--s) * 2)) / 3);
  transition: transform 0.1s linear;
}
@media not screen and (min-width: 1024px) {
  .windowcardsItem {
    width: calc(calc(100% - calc(var(--s) * 1)) / 2);
  }
}
@media not screen and (min-width: 768px) {
  .windowcardsItem {
    width: calc(calc(100% - calc(var(--s) * 0)) / 1);
  }
}
.windowcardsItem:nth-of-type(odd):hover {
  transform: rotate(2.5deg);
}
.windowcardsItem:nth-of-type(even):hover {
  transform: rotate(-2.5deg);
}
.homeSectionFoot {
  display: flex;
  justify-content: flex-end;
}
.homeSectionLink {
  font-size: 0.8rem;
  display: flex;
  gap: calc(0.5rem * 0.5);
  background: linear-gradient(currentcolor, currentcolor) left bottom / 100% 1px
    no-repeat;
  transition: background-size 0.4s cubic-bezier(0.215, 0.61, 0.355, 1);
}
.homeSectionLink:hover {
  background-position: right bottom;
  background-size: 0 1px;
}
.homeSectionLinkIcon {
  width: 0.8rem;
  height: auto;
}
</style>
