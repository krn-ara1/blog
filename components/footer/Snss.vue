<script setup>
import { snss } from "~/data/data";
</script>

<template>
  <ul class="snssContainer">
    <FooterSns v-for="(sns, index) in snss" :key="index" :sns="sns" />
  </ul>
</template>

<style scoped>
.snssContainer {
  display: flex;
  gap: calc(0.8rem * 0.8);
  flex-wrap: wrap;
}
</style>
