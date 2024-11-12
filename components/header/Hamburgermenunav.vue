<script setup>
import { pages } from '~/data/data';
</script>

<template>
  <nav class="navContainer">
    <h2 class="navHead">ナビゲーションメニュー</h2>
    <ul class="navBody">
      <HeaderHamburgermenunavitem
        v-for="(page, index) in pages"
        :key="index"
        :page="page"
      />
    </ul>
  </nav>
</template>

<style scoped>
.navContainer {
  width: 100%;
  display: flex;
}
.navHead {
  display: none;
}
.navBody {
  width: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  gap: 0.8rem;
}
</style>
