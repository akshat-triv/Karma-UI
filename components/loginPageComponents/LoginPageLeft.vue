<template>
  <div class="loginPageLeft">
    <div class="loginPageLeftContentWrapper">
      <div class="welcomeImageWrapper">
        <inline-svg
          :src="require('@/assets/svg/peace-mountain.svg')"
          class="welcomeImage"
        ></inline-svg>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'LoginPageLeft',
}
</script>

<style lang="scss">
.welcomeImage {
  .circles {
    fill: var(--surface2);
  }
  .human {
    animation: hover 2s linear infinite;
  }

  @keyframes hover {
    0% {
      transform: translateY(0);
    }

    25% {
      transform: translateY(3px);
    }

    75% {
      transform: translateY(-3px);
    }

    100% {
      transform: translateY(0);
    }
  }
}
</style>

<style lang="scss" scoped>
.loginPageLeft {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  background: var(--surface3);
  flex: 0 0 65%;
}

.welcomeImage {
  width: 100%;
  height: 100%;
  object-fit: cover;
  color: var(--surface3);

  &Wrapper {
    width: 70rem;
    height: 45rem;
  }
}
</style>
