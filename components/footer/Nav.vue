<script setup>
import { pages } from "~/data/data";
</script>

<template>
  <nav class="navContainer">
    <h2 class="navHead">ナビゲーションメニュー</h2>
    <ul class="navBody">
      <FooterNavitem v-for="(page, index) in pages" :key="index" :page="page" />
    </ul>
  </nav>
</template>
<style scoped>
.navContainer {
  display: flex;
}
.navHead {
  display: none;
}
.navBody {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 0.8rem;
}
</style>
