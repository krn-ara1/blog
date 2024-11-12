<script setup>
import WindowcardWindowcard from "@/components/windowcard/Windowcard.vue";

import { pickupTrips } from "~/data/data";
</script>

<template>
  <div class="homeContainer">
    <!-- 旅行セクション -->
    <section id="trip" class="homeSection trip">
      <div class="homeSectionWrapper">
        <hgroup class="homeSectionHead">
          <h2 class="homeSectionTitle">旅行</h2>
          <span class="homeSectionTitleEn">trip</span>
        </hgroup>
        <div class="homeSectionBody">
          <ul class="windowcardsContainer">
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
}
.homeSectionWrapper {
  width: 80%;
  max-width: 1024px;
  margin: 0 auto;
  display: flex;
  flex-direction: column;
  gap: var(--xs);
}
.homeSectionHead {
  display: flex;
  align-items: baseline;
  gap: 0.5rem;
}
.homeSectionTitle {
  font-size: 1.4rem;
}
.homeSectionTitleEn {
  font-size: 1rem;
  text-transform: uppercase;
}
.homeSectionBody {
}
.windowcardsContainer {
  display: flex;
  gap: var(--xs);
  flex-wrap: wrap;
}
.windowcardsItem {
  width: calc(calc(100% - calc(var(--xs) * 2)) / 3);
}
@media screen and (max-width: 810px) {
  .windowcardsItem {
    width: calc(calc(100% - calc(var(--xs) * 1)) / 2);
  }
}
@media screen and (max-width: 430px) {
  .windowcardsItem {
    width: calc(calc(100% - calc(var(--xs) * 0)) / 1);
  }
}
.homeSectionFoot {
  display: flex;
  justify-content: flex-end;
}
.homeSectionLink {
  font-size: 0.8rem;
  display: flex;
  gap: calc(0.5rem * 0.5);
}
.homeSectionLinkIcon {
  width: 0.8rem;
  height: auto;
}
</style>
