<script setup>
import { ref, watch } from 'vue'
import { useRoute } from 'vue-router'
import LogoIcon from './icons/LogoIcon.vue'
import HamburgerIcon from './icons/HamburgerIcon.vue'

const route = useRoute()
const isMobileDrawerMenuOpen = ref(false)

watch(
  () => route.path,
  () => (isMobileDrawerMenuOpen.value = false),
)
</script>

<template>
  <!-- DESKTOP VERSION -->
  <header class="hidden-sm-and-down">
    <ElRow class="menu">
      <ElCol :span="11" class="menu-wrapper">
        <RouterLink
          to="/"
          class="big-link"
          :class="{ 'active-big-link': route.path === '/' }"
          v-motion-slide-left
          :duration="1500"
          :delay="500"
          >NASLOVNICA</RouterLink
        >
        <RouterLink
          to="/about"
          class="big-link"
          :class="{ 'active-big-link': route.path === '/about' }"
          v-motion-slide-left
          :duration="1500"
          :delay="1000"
          >O NAMA</RouterLink
        >
      </ElCol>
      <ElCol :span="2" align="center" v-motion-slide-bottom :duration="1500">
        <ElIcon class="logo-wrapper">
          <RouterLink to="/">
            <LogoIcon class="logo" />
          </RouterLink>
        </ElIcon>
      </ElCol>
      <ElCol :span="11" align="end" class="menu-wrapper">
        <RouterLink
          to="/gallery"
          class="big-link"
          :class="{ 'active-big-link': route.path === '/gallery' }"
          v-motion-slide-right
          :duration="1500"
          :delay="1500"
          >GALERIJA</RouterLink
        >
        <RouterLink
          to="/contact"
          class="big-link"
          :class="{ 'active-big-link': route.path === '/contact' }"
          v-motion-slide-right
          :duration="1500"
          :delay="2000"
          >KONTAKT</RouterLink
        >
      </ElCol>
    </ElRow>
  </header>

  <!-- MOBILE VERSION -->
  <header class="hidden-md-and-up" v-motion-slide-top :duration="1000">
    <ElRow class="mobile-header" justify="space-between" align="middle">
      <ElCol :span="6" v-motion-slide-top :duration="1500">
        <ElIcon size="28" class="hamburger-icon" @click="isMobileDrawerMenuOpen = true">
          <HamburgerIcon style="color: var(--el-color-primary)" />
        </ElIcon>
      </ElCol>
      <ElCol align="middle" :span="12" v-motion-slide-top :duration="1500" :delay="500">
        <RouterLink to="/" style="color: var(--el-color-primary); text-decoration: none">
          <h2>House of Cheetah</h2>
        </RouterLink>
      </ElCol>
      <ElCol :span="6" align="end" v-motion-slide-top :duration="1500" :delay="1000">
        <RouterLink to="/">
          <LogoIcon style="height: 50px; width: auto; color: var(--el-color-primary)" />
        </RouterLink>
      </ElCol>
    </ElRow>
  </header>

  <!-- MOBILE DRAWER -->
  <ElDrawer v-model="isMobileDrawerMenuOpen" direction="ltr" size="100%">
    <template #header>
      <ElRow>
        <h3 style="color: white">House of Cheetah</h3>
      </ElRow>
    </template>

    <template #default>
      <div class="drawer-container">
        <RouterLink
          to="/"
          class="el-button drawer-button"
          :class="{
            'el-button--primary': 'index' === route.name,
          }"
        >
          <ElRow class="drawer-button-text-wrapper" align="middle" justify="center">
            NASLOVNICA
          </ElRow>
        </RouterLink>
        <RouterLink
          to="/about"
          class="el-button drawer-button"
          :class="{
            'el-button--primary': 'index' === route.name,
          }"
        >
          <ElRow class="drawer-button-text-wrapper" align="middle" justify="center"> O NAMA </ElRow>
        </RouterLink>
        <RouterLink
          to="/gallery"
          class="el-button drawer-button"
          :class="{
            'el-button--primary': 'index' === route.name,
          }"
        >
          <ElRow class="drawer-button-text-wrapper" align="middle" justify="center">
            GALERIJA
          </ElRow>
        </RouterLink>
        <RouterLink
          to="/contact"
          class="el-button drawer-button"
          :class="{
            'el-button--primary': 'index' === route.name,
          }"
        >
          <ElRow class="drawer-button-text-wrapper" align="middle" justify="center">
            KONTAKT
          </ElRow>
        </RouterLink>
      </div>
    </template>

    <template #footer>
      <ElRow justify="center" align="middle" class="">
        <ElButton class="w-100 drawer-button" plain @click="isMobileDrawerMenuOpen = false">
          <ElRow class="drawer-button-text-wrapper" align="middle" justify="center"> IZLAZ </ElRow>
        </ElButton>
      </ElRow>
    </template>
  </ElDrawer>
</template>

<style scoped>
header {
  opacity: 0.95;
  border-bottom-left-radius: 4px;
  border-bottom-right-radius: 4px;
}

/* DESKTOP VERSION */
.menu {
  height: 150px;
  padding: 0 24px;
}
.menu-wrapper {
  margin: auto 0 auto 0;
}
.big-link {
  position: relative;
  margin-right: 16px;
  font-weight: 600;
  font-size: 16px;
  text-decoration: none;
  color: var(--el-color-primary);
  letter-spacing: 1.2px;
}
.big-link::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -8px;
  width: 0;
  height: 2px;
  background-color: var(--el-color-primary);
  transition: width 200ms ease-in-out;
}
.big-link:hover::after {
  width: 100%;
}
.active-big-link::after {
  content: '';
  position: absolute;
  left: 0;
  bottom: -8px;
  width: 100%;
  height: 2px;
  background-color: var(--el-color-primary);
}
.logo-wrapper {
  margin-top: 10px;
  height: 120px;
  width: 100%;
  color: var(--el-color-primary);
}
.logo {
  width: auto;
  height: 70px !important;
  color: var(--el-color-primary);
}
.flag-icon {
  width: 30px;
  height: 22px;
}
svg {
  color: white;
}
button {
  background-color: transparent;
}

@media (max-width: 1350px) {
  .menu {
    height: 70px;
  }
  .big-link {
    font-size: 14px;
  }
  .logo-wrapper {
    height: 60px;
    width: 100%;
    color: var(--el-color-primary);
  }
  .logo {
    height: 55px;
    color: var(--el-color-primary);
  }
}

/* MOBILE VERSION */

.mobile-header {
  height: 60px;
  padding: 8px 16px;
}
.hamburger-icon {
  cursor: pointer;
}
.mobile-flag-icon {
  height: 40px;
}
.drawer-container {
  display: flex;
  flex-direction: column;
  gap: 8px;
}
.drawer-button {
  color: var(--el-color-primary);
  --el-button-hover-border-color: var(--el-color-primary);
  background-color: white;
  height: 45px;
  font-weight: 700;
  text-decoration: none;
  margin: 0 !important;
  border-radius: 8px;
}
.drawer-button:hover {
  background-color: #403f45;
}
.drawer-button-text-wrapper {
  width: 100%;
  gap: 12px;
  font-weight: 600;
  letter-spacing: 1px;
}
</style>
