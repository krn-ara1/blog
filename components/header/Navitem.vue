<script setup>
const props = defineProps({
  page: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <li>
    <NuxtLink class="navItemContainer" :to="props.page.path">
      <span class="navItemJa">{{ props.page.jaText }}</span>
      <span class="navItemEn">{{ props.page.enText }}</span>
    </NuxtLink>
  </li>
</template>

<style scoped>
.navItemContainer {
  background-color: #ffffff;
  padding: calc(0.8rem * 0.2) calc(0.8rem * 1);
  border: 1px solid var(--color-text);
  border-radius: 99999px;
  display: flex;
  align-items: center;
  gap: calc(0.8rem * 0.5);
  transition: all 0.4s linear;
}
.navItemContainer:hover,
.navItemContainer:focus {
  background-color: var(--color-text);
  color: var(--color-bg);
  transition: all 0.1s linear;
}
.navItemJa {
  text-wrap: nowrap;
}
.navItemEn {
  text-wrap: nowrap;
  text-transform: uppercase;
  font-weight: lighter;
}
@media not screen and (min-width: 1080px) {
  .navItemEn {
    display: none;
  }
}
</style>
