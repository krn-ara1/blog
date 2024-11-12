<script setup>
const props = defineProps({
  sns: {
    type: Object,
    required: true,
  },
});
const snsIconStyle = {
  background: props.sns.color,
};
</script>

<template>
  <li>
    <NuxtLink
      class="snsContainer"
      :to="props.sns.path"
      rel="noopener"
      target="_blank"
      :style="snsIconStyle"
    >
      <span class="snsIcon">
        <img
          :alt="props.sns.name"
          class="snsIconImage"
          :src="props.sns.iconPath"
          width="35"
          height="35"
        />
      </span>
      <span class="snsText">{{ props.sns.id }}</span>
    </NuxtLink>
  </li>
</template>

<style scoped>
.snsContainer {
  color: var(--color-bg);
  font-weight: lighter;
  display: flex;
  align-items: center;
  gap: calc(0.8rem * 0.2);
  border-radius: 99999px;
  padding: 0 calc(0.8rem * 0.8);
  filter: grayscale(1);
  transition: filter 0.4s;
}
.snsContainer:hover,
.snsContainer:focus {
  filter: grayscale(0);
  transition: filter 0.2s;
}
.snsIcon {
  width: calc(0.8rem + 0.8rem * 0.2 * 2);
  height: calc(0.8rem + 0.8rem * 0.2 * 2);
  padding: 1px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.snsIconImage {
  width: 80%;
  height: auto;
}
.snsText {
}
</style>
