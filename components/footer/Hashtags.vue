<script setup>
import { hashtags } from '~/data/data';
</script>

<template>
  <ul class="hashtagsContainer">
    <FooterHashtag
      v-for="(hashtag, index) in hashtags"
      :key="index"
      :hashtag="hashtag"
    />
  </ul>
</template>

<style scoped>
.hashtagsContainer {
  display: flex;
  gap: 0 calc(0.8rem * 0.8);
  flex-wrap: wrap;
}
</style>
