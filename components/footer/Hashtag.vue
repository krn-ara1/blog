<script setup>
const props = defineProps({
  hashtag: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <NuxtLink class="hashtagContainer" :to="props.hashtag.path">
    <span>#</span>
    <span class="hashtagText">{{ props.hashtag.text }}</span>
    <span class="hashtagEmoji">{{ props.hashtag.emoji }}</span>
  </NuxtLink>
</template>

<style scoped>
.hashtagContainer {
  display: flex;
  align-items: center;
  gap: calc(0.8rem * 0.2);
}
.hashtagContainer:hover,
.hashtagContainer:focus {
  text-decoration: underline;
}
.hashtagText {
}
.hashtagEmoji {
  color: transparent;
  text-shadow: 0 0 0 var(--text);
}
.hashtagContainer:hover .hashtagEmoji,
.hashtagContainer:focus .hashtagEmoji {
  color: initial;
  text-shadow: initial;
}
</style>
