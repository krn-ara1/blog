<script setup>
import WindowcardWindowcard from "@/components/windowcard/Windowcard.vue";
import MemocardMemocard from "@/components/memocard/Memocard.vue";
import BubbleTrip from "@/assets/svg/bubble_03.svg";
import BubbleHangout from "@/assets/svg/bubble_02.svg";

import { pickupTrips } from "~/data/data";
import { pickupHangouts } from "~/data/data";

// 領域に入ってきたら表示する
import { useIntersectionObserver } from "~/composables/useIntersectionObserver";
const trip = ref(null);
const hangout = ref(null);
const triplist = ref(null);
const hangoutlist = ref(null);
const elements = [
  // trip,
  // hangout,
  triplist,
  hangoutlist,
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
    <!-- 散策セクション -->
    <section id="hangout" class="homeSection hangout -once" ref="hangout">
      <div class="homeSectionWrapper">
        <hgroup class="homeSectionHead">
          <BubbleHangout
            class="homeSectionHeadBackground"
            preserveAspectRatio="none"
          />
          <h2 class="homeSectionTitle">散策</h2>
          <span class="homeSectionTitleEn">hangout</span>
        </hgroup>
        <div class="homeSectionBody">
          <ul class="memocardsContainer -once" ref="hangoutlist">
            <li
              class="memocardsItem"
              v-for="(pickupHangout, index) in pickupHangouts"
              :key="index"
            >
              <MemocardMemocard :article="pickupHangout" />
            </li>
          </ul>
        </div>
        <div class="homeSectionFoot">
          <NuxtLink class="homeSectionLink" href="#"
            >散策の記事をすべて見る<img
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
  display: flex;
  flex-direction: column;
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
.hangout .homeSectionHeadBackground {
  width: calc(var(--xs) * 2 + 0.5rem + 1.4rem * 2 + 1rem * 7);
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
.memocardsContainer {
  display: flex;
  gap: var(--s);
  flex-wrap: wrap;
}
.memocardsItem {
  position: relative;
  width: calc(calc(100% - calc(var(--s) * 2)) / 3);
  transition: scale 0.3s ease-out;
}
@media not screen and (min-width: 1024px) {
  .memocardsItem {
    width: calc(calc(100% - calc(var(--s) * 1)) / 2);
  }
}
@media not screen and (min-width: 768px) {
  .memocardsItem {
    width: calc(calc(100% - calc(var(--s) * 0)) / 1);
  }
}
.memocardsItem::before {
  z-index: 2;
  position: absolute;
  top: -20px;
  left: 50%;
  content: "";
  display: inline-block;
  background-repeat: no-repeat;
  background-position: center center;
  background-size: contain;
  aspect-ratio: 130 / 50;
  width: 130px;
  height: auto;
}
.memocardsItem:nth-of-type(7n)::before {
  background-image: url(icon_tape_blue.png);
}
.memocardsItem:nth-of-type(7n + 1)::before {
  background-image: url(icon_tape_blue.png);
}
.memocardsItem:nth-of-type(7n + 2)::before {
  background-image: url(icon_tape_orange.png);
}
.memocardsItem:nth-of-type(7n + 3)::before {
  background-image: url(icon_tape_blue.png);
}
.memocardsItem:nth-of-type(7n + 4)::before {
  background-image: url(icon_tape_white.png);
}
.memocardsItem:nth-of-type(7n + 5)::before {
  background-image: url(icon_tape_orange.png);
}
.memocardsItem:nth-of-type(7n + 6)::before {
  background-image: url(icon_tape_blue.png);
}
.memocardsItem:nth-of-type(5n)::before {
  transform: translateX(-50%) rotate(6deg);
}
.memocardsItem:nth-of-type(5n + 1)::before {
  transform: translateX(-50%) rotate(5deg);
}
.memocardsItem:nth-of-type(5n + 2)::before {
  transform: translateX(-50%) rotate(0deg);
}
.memocardsItem:nth-of-type(5n + 3)::before {
  transform: translateX(-50%) rotate(9deg);
}
.memocardsItem:nth-of-type(5n + 4)::before {
  transform: translateX(-50%) rotate(12deg);
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
