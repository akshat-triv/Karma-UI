<template>
  <nav class="verticalNavigation">
    <div class="navigationItemCollection">
      <div class="navigationItem">
        <div class="navigationItemIconWrapper">
          <inline-svg
            :src="require('@/assets/svg/notifications.svg')"
            class="navigationItemIcon"
          ></inline-svg>
        </div>
        <span class="navigationItemText">Activity</span>
      </div>
      <div class="navigationItem">
        <div class="navigationItemIconWrapper">
          <inline-svg
            :src="require('@/assets/svg/projects.svg')"
            class="navigationItemIcon"
          ></inline-svg>
        </div>
        <span class="navigationItemText">Projects</span>
      </div>
      <div class="navigationItem">
        <div class="navigationItemIconWrapper gridSize24">
          <inline-svg
            :src="require('@/assets/svg/chats.svg')"
            class="navigationItemIcon"
          ></inline-svg>
        </div>
        <span class="navigationItemText">Chats</span>
      </div>
      <div class="navigationItem">
        <div class="navigationItemIconWrapper gridSize24">
          <inline-svg
            :src="require('@/assets/svg/groups.svg')"
            class="navigationItemIcon"
          ></inline-svg>
        </div>
        <span class="navigationItemText">Channels</span>
      </div>
      <div class="navigationItem">
        <div class="navigationItemIconWrapper">
          <inline-svg
            :src="require('@/assets/svg/calendar.svg')"
            class="navigationItemIcon"
          ></inline-svg>
        </div>
        <span class="navigationItemText">Calendar</span>
      </div>
    </div>
    <div class="navigationItemCollection">
      <div class="navigationItem secondary encircled">
        <div class="navigationItemIconWrapper gridSize32">
          <inline-svg
            v-if="themeLight"
            :src="require('@/assets/svg/sun.svg')"
            class="navigationItemIcon"
            @click="changeTheme(false)"
          ></inline-svg>
          <inline-svg
            v-else
            :src="require('@/assets/svg/moon.svg')"
            class="navigationItemIcon"
            @click="changeTheme(true)"
          ></inline-svg>
        </div>
      </div>
      <div class="navigationItem secondary">
        <div class="navigationItemIconWrapper">
          <inline-svg
            :src="require('@/assets/svg/settings.svg')"
            class="navigationItemIcon"
          ></inline-svg>
        </div>
        <span class="navigationItemText">Settings</span>
      </div>
    </div>
  </nav>
</template>

<script>
import { inject } from '@nuxtjs/composition-api'

export default {
  name: 'VerticalNavigation',
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
.verticalNavigation {
  height: 100%;
  width: 6rem;
  padding: 1rem;
  background: var(--surface1);
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-direction: column;
}

.navigationItem {
  &Collection {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    width: 100%;
  }

  &.encircled {
    clip-path: circle(50%);
    padding: 0.5rem 0;
    background-color: var(--surface2);
    display: flex;
    justify-content: center;
    align-items: center;
  }

  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
  color: var(--text1);
  transition: color 0.3s;

  &.secondary {
    color: var(--text2);
  }

  &:hover {
    cursor: pointer;
    color: var(--text1);
  }

  &:not(:last-of-type) {
    margin-bottom: 2rem;
  }

  &Icon {
    color: currentColor;
    width: 100%;
    height: 100%;

    &Wrapper {
      width: 2rem;
      height: 2rem;
      color: currentColor;

      &:not(:last-child) {
        margin-bottom: 0.5rem;
      }

      &.gridSize24 {
        width: 2.4rem;
        height: 2.4rem;
      }

      &.gridSize32 {
        width: 3.2rem;
        height: 3.2rem;
      }
    }
  }

  &Text {
    font-size: 1.2rem;
    font-weight: 400;
    color: currentColor;
  }
}
</style>
