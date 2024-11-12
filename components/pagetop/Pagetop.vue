<script setup>
const isScrolledDown = ref(false);
onMounted(() => {
  window.addEventListener("scroll", () => {
    const scrollY = window.scrollY;
    if (scrollY >= 200) {
      isScrolledDown.value = true;
    } else {
      isScrolledDown.value = false;
    }
  });
});
const scrollPageTop = () => {
  window.scrollTo({
    top: 0,
    behavior: "smooth",
  });
};
</script>

<template>
  <div class="pagetopContainer">
    <div class="pagetopWrapper">
      <button
        id="pagetopButton"
        :class="['pagetopButton', isScrolledDown && 'isDisplayed']"
        @click="scrollPageTop"
      >
        <span class="pagetopButtonText">page top</span>
      </button>
    </div>
  </div>
</template>

<style scoped>
.pagetopContainer {
  width: 100%;
  position: sticky;
  bottom: 0;
}
.pagetopWrapper {
  width: 80%;
  max-width: 1024px;
  margin: 0 auto;
  padding: calc(0.8rem * 1) 0;
  display: flex;
  justify-content: flex-end;
}
.pagetopButton {
  background-color: var(--bg);
  transform: translateX(100%);
  font-size: 0.8rem;
  text-transform: uppercase;
  border: 1px solid var(--text);
  border-radius: 99999px;
  padding: calc(0.8rem * 0.2) calc(0.8rem * 1);
  cursor: pointer;
  animation: fadeOut forwards 1s;
  display: flex;
  align-items: center;
  gap: calc(0.8rem * 0.2);
  height: calc(0.8rem * 1.6 + 0.8rem * 0.2);
}
.pagetopButtonText {
}
.pagetopButton::after {
  content: "";
  display: inline-block;
  width: 0.8rem;
  height: 0.8rem;
  background-image: url(/icon_pagetop.png);
  background-position: center;
  background-size: contain;
}
@keyframes fadeOut {
  0% {
    opacity: 1;
  }
  1% {
    opacity: 1;
  }
  30% {
    opacity: 1;
  }
  100% {
    display: none;
    opacity: 0;
  }
}
.pagetopButton.isDisplayed {
  animation: fadeIn forwards 1s;
}
@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  1% {
    display: block;
    opacity: 0;
  }
  30% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
@media screen and (max-width: 1280px) {
  .pagetopButton {
    transform: translateX(0);
  }
  .pagetopButtonText {
    display: none;
  }
}
</style>
