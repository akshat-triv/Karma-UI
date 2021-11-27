<template>
  <div class="loginPageWrapper">
    <login-page-left></login-page-left>
    <login-page-right></login-page-right>
    <span class="copyrightText">&copy; by Akatsuki. All rights reserved.</span>
  </div>
</template>

<style lang="scss" scoped>
.loginPageWrapper {
  display: flex;
  width: 100%;
  height: calc(100% - 6.8rem);
}

.copyrightText {
  position: absolute;
  bottom: 1rem;
  left: 1rem;
  font-size: 1.4rem;
  color: var(--text2Opaq);
}
</style>
