<script setup>
const isOpened = ref(false);
const onClick = () => {
  isOpened.value = !isOpened.value;
};
onMounted(() => {
  window.addEventListener("resize", () => {
    const innerWidth = window.innerWidth;
    if (innerWidth >= 811) {
      isOpened.value = false;
    }
  });
});
</script>

<template>
  <button
    :class="['hamburgermenuButtonContainer', isOpened && 'isOpened']"
    @click="onClick"
  >
    <span></span>
    <span></span>
    <span></span>
  </button>
  <menu :class="['hamburgermenuMenuContainer', isOpened && 'isOpened']">
    <HeaderHamburgermenunav />
    <HeaderHamburgermenusearch />
  </menu>
</template>

<style scoped>
.hamburgermenuButtonContainer {
  background-color: transparent;
  border: none;
  position: relative;
  width: 25px;
  height: 20px;
  cursor: pointer;
}
.hamburgermenuButtonContainer span {
  position: absolute;
  left: 0;
  width: 100%;
  height: 2px;
  background-color: var(--color-text);
  border-radius: 99999px;
}
.hamburgermenuButtonContainer,
.hamburgermenuButtonContainer span {
  display: inline-block;
  transition: all 0.5s;
  box-sizing: border-box;
}
.hamburgermenuButtonContainer span:nth-of-type(1) {
  top: 15%;
}
.hamburgermenuButtonContainer span:nth-of-type(2) {
  top: 55%;
}
.hamburgermenuButtonContainer span:nth-of-type(3) {
  bottom: -5%;
}
.hamburgermenuButtonContainer span:nth-of-type(1) {
  animation: transformTopBarToHamburger 0.75s forwards;
}
@keyframes transformTopBarToHamburger {
  0% {
    transform: translateY(8.5px) rotate(45deg);
  }
  50% {
    transform: translateY(8.5px) rotate(0);
  }
  100% {
    transform: translateY(0) rotate(0);
  }
}
.hamburgermenuButtonContainer span:nth-of-type(2) {
  transition: all 0.25s 0.25s;
  opacity: 1;
}
.hamburgermenuButtonContainer span:nth-of-type(3) {
  animation: transformBottomBarToHamburger 0.75s forwards;
}
@keyframes transformBottomBarToHamburger {
  0% {
    transform: translateY(-8px) rotate(-45deg);
  }
  50% {
    transform: translateY(-8px) rotate(0);
  }
  100% {
    transform: translateY(0) rotate(0);
  }
}
.hamburgermenuButtonContainer.isOpened span:nth-of-type(1) {
  animation: transformTopBarToBatten 0.75s forwards;
}
@keyframes transformTopBarToBatten {
  0% {
    transform: translateY(0) rotate(0);
  }
  50% {
    transform: translateY(8.5px) rotate(0);
  }
  100% {
    transform: translateY(8.5px) rotate(45deg);
  }
}
.hamburgermenuButtonContainer.isOpened span:nth-of-type(2) {
  opacity: 0;
}
.hamburgermenuButtonContainer.isOpened span:nth-of-type(3) {
  animation: transformBottomBarToBatten 0.75s forwards;
}
@keyframes transformBottomBarToBatten {
  0% {
    transform: translateY(0) rotate(0);
  }
  50% {
    transform: translateY(-8px) rotate(0);
  }
  100% {
    transform: translateY(-8px) rotate(-45deg);
  }
}
.hamburgermenuMenuContainer {
  background-color: rgba(237, 181, 96, 0.7);
  z-index: 99999;
  height: calc(
    100vh -
      ((0.8rem * 1 * 2) + (0.8rem * 0.5) + (0.8rem * 1.6 * 2) + (0.8rem * 2) + (0.8rem))
  );
  position: absolute;
  bottom: 0;
  right: 50%;
  transform-origin: top;
  transform: translateY(calc(100% + 0.8rem * 1)) translateX(50%) rotateX(90deg);
  width: 80%;
  /* border: 1px solid var(--color-text); */
  border-radius: calc(0.8rem * 1);
  transition: transform 0.4s;
  /* padding: calc(0.8rem * 1); */
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
  overflow-y: scroll;
  padding: 0.8rem;
}
.hamburgermenuMenuContainer::-webkit-scrollbar {
  width: 10px;
}

.hamburgermenuMenuContainer::-webkit-scrollbar-track {
  border-radius: 9999px;
}

.hamburgermenuMenuContainer::-webkit-scrollbar-thumb {
  background-color: rgba(237, 181, 96, 0.4);
  border-radius: 25px;
}
.hamburgermenuMenuContainer::-webkit-scrollbar-thumb:hover {
  background-color: rgba(237, 181, 96, 0.8);
  transition: background-color 4s linear;
}
.hamburgermenuMenuContainer.isOpened {
  transform: translateY(calc(100% + 0.8rem * 1)) translateX(50%) rotateX(0);
  transition: transform 0.4s;
}
@media screen and (min-width: 811px) {
  .hamburgermenuButtonContainer {
    display: none;
  }
}
</style>
