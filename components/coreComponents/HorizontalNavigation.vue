<template>
  <nav class="horizontalNavigationWrapper">
    <div class="horizontalNavigation globalMarginWrapper">
      <div class="karmaLogoWrapper">
        <inline-svg
          :src="require('@/assets/svg/karma-logo.svg')"
          class="karmaLogo"
        ></inline-svg>
      </div>
      <div class="themeIconWrapper">
        <inline-svg
          v-if="themeLight"
          :src="require('@/assets/svg/sun.svg')"
          class="themeIcon"
          @click="changeTheme(false)"
        ></inline-svg>
        <inline-svg
          v-else
          :src="require('@/assets/svg/moon.svg')"
          class="themeIcon"
          @click="changeTheme(true)"
        ></inline-svg>
      </div>
    </div>
  </nav>
</template>

<script>
import { inject } from '@nuxtjs/composition-api'

export default {
  name: 'HorizontalNavigation',
  setup() {
    const themeLight = inject('themeLight')
    const changeTheme = inject('changeTheme')

    return {
      themeLight,
      changeTheme,
    }
  },
}
</script>

<style lang="scss" scoped>
.horizontalNavigation {
  display: flex;
  align-items: center;

  &Wrapper {
    padding: 1rem 0;
    background: var(--surface1);
    height: 6.8rem;
    border-bottom: 1px solid var(--surface3);
  }

  .karmaLogo {
    color: var(--text1);
    width: 100%;
    height: 100%;

    &Wrapper {
      width: 10rem;
      height: 4.8rem;
      display: inline-block;
      margin-right: auto;
    }
  }

  .themeIcon {
    color: var(--text2);
    width: 100%;
    height: 100%;

    &Wrapper {
      width: 4rem;
      height: 4rem;
      display: inline-block;

      &:hover {
        cursor: pointer;
        .themeIcon {
          color: var(--text1);
        }
      }
    }
  }
}
</style>
