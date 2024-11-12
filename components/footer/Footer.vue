<template>
  <footer id="footer" class="footerContainer">
    <div class="footerWrapper">
      <div class="footerHead">
        <NuxtLink class="footerLogo" to="/">
          <img
            alt="ittari kitari"
            class="footerLogoImage"
            src="/logo_column.png"
            width="236"
            height="128"
          />
        </NuxtLink>
        <div class="footerNavAndSearch">
          <FooterNav />
          <FooterSearch />
        </div>
      </div>
      <div class="footerBody">
        <FooterHashtags />
        <FooterSnss />
      </div>
      <div class="footerFoot">
        <FooterCopyrights />
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footerContainer {
  position: sticky;
  top: 100vh;
  width: 100%;
  font-size: 0.8rem;
  background-color: var(--main);
  border-top: 1px solid var(--text);
  margin-top: calc(0.8rem * 1);
}
.footerWrapper {
  width: 80%;
  max-width: 1024px;
  margin: 0 auto;
  padding: calc(0.8rem * 2) 0;
  display: flex;
  flex-direction: column;
  gap: calc(0.8rem * 2);
}
.footerHead {
  display: flex;
  align-items: center;
  gap: calc(0.8rem * 2);
}
.footerLogo {
  align-self: start;
  width: 140px;
  height: auto;
  display: flex;
  align-items: center;
}
.footerLogoImage {
  width: 100%;
  height: auto;
}
.footerNavAndSearch {
  display: flex;
  flex-direction: column;
  gap: calc(0.8rem * 1);
}
.footerBody {
  display: flex;
  flex-direction: column;
  gap: calc(0.8rem * 2);
}
.footerFoot {
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
