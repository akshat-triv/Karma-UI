<template>
  <div id="app">
    <header-navigation></header-navigation>
    <Nuxt />
  </div>
</template>

<script>
import { ref, watch, provide } from '@nuxtjs/composition-api'
import headerNavigation from '@/components/coreComponents/HeaderNavigation.vue'

export default {
  components: {
    headerNavigation,
  },
  setup() {
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
    }
  },
}
</script>
