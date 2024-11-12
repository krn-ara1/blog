<script setup>
import HeaderHeader from '@/components/header/Header.vue';
import PagetopPagetop from '@/components/pagetop/Pagetop.vue';
import FooterFooter from '@/components/footer/Footer.vue';
</script>

<template>
  <div class="container">
    <HeaderHeader />
    <div class="wrapper">
      <div class="mainAndPageTop">
        <main class="main">
          <slot />
        </main>
        <PagetopPagetop />
      </div>
      <FooterFooter />
    </div>
  </div>
</template>

<style scoped>
.container {
}
.wrapper {
  min-height: 100vh;
  padding-top: calc(
    (0.8rem * 1.6 + 0.8rem * 1.6 * 0.2 * 2) * 2 + (0.8rem * 0.5) + (0.8rem * 1) *
      2
  );
  display: flex;
  flex-direction: column;
}
.mainAndPageTop {
  flex-grow: 1;
}
.main {
  width: 100%;
  overflow-x: hidden;
  font-size: 1rem;
}
</style>
