<template>
  <div
    id="app"
    :class="{
      horizontalLayout: horizontalLayout,
      verticalLayout: !horizontalLayout,
    }"
  >
    <horizontal-navigation v-if="horizontalLayout"></horizontal-navigation>
    <vertical-navigation v-else></vertical-navigation>
    <Nuxt />
  </div>
</template>

<script>
import { ref, watch, provide, useRoute } from '@nuxtjs/composition-api'
import HorizontalNavigation from '~/components/coreComponents/HorizontalNavigation.vue'
import VerticalNavigation from '~/components/coreComponents/VerticalNavigation.vue'

export default {
  components: {
    HorizontalNavigation,
    VerticalNavigation,
  },
  setup() {
    const route = useRoute()
    const horizontalLayout = route.value.path === '/'
    const themeLight = ref(false)

    watch(themeLight, changeTheme)

    if (!process.server) changeTheme(themeLight.value)

    function changeTheme(value) {
      if (themeLight.value !== value) themeLight.value = value

      document.documentElement.classList.replace(
        value ? 'dark' : 'light',
        value ? 'light' : 'dark'
      )
    }

    provide('themeLight', themeLight)
    provide('changeTheme', changeTheme)

    return {
      themeLight,
      horizontalLayout,
    }
  },
}
</script>

<style lang="scss">
#app {
  height: 100vh;

  &.verticalLayout {
    display: flex;
  }
}
</style>
