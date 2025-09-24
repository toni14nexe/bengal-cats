<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import CatIcon from './icons/CatIcon.vue'
import DollarIcon from './icons/DollarIcon.vue'
import LogoIcon from './icons/LogoIcon.vue'
import ShakeHandsIcon from './icons/ShakeHandsIcon.vue'
import DocumentIcon from './icons/DocumentIcon.vue'

const containerRef = ref(null)
const isVisible = ref(false)
let observer = null

onMounted(() => {
  observer = new IntersectionObserver(
    ([entry]) => {
      if (entry.isIntersecting) {
        isVisible.value = true
        observer.unobserve(entry.target)
      }
    },
    { threshold: 0.1 },
  )
  if (containerRef.value) observer.observe(containerRef.value)
})

onUnmounted(() => {
  if (containerRef.value && observer) {
    observer.unobserve(containerRef.value)
  }
})
</script>

<template>
  <footer ref="containerRef">
    <template v-if="isVisible">
      <ElRow>
        <ElCol
          :xs="24"
          :sm="12"
          :md="6"
          align="center"
          class="widget-wrapper"
          v-motion-slide-bottom
          :duration="1000"
        >
          <ElIcon class="icon-wrapper">
            <CatIcon class="icon" />
          </ElIcon>
          <p class="footer-text">Uzgoj</p>
        </ElCol>
        <ElCol
          :xs="24"
          :sm="12"
          :md="6"
          align="center"
          class="widget-wrapper"
          v-motion-slide-bottom
          :duration="1000"
          :delay="250"
        >
          <ElIcon class="icon-wrapper">
            <DollarIcon class="icon" />
          </ElIcon>
          <p class="footer-text">Prodaja</p>
        </ElCol>
        <ElCol
          :xs="24"
          :sm="12"
          :md="6"
          align="center"
          class="widget-wrapper"
          v-motion-slide-bottom
          :duration="1000"
          :delay="500"
        >
          <ElIcon class="icon-wrapper">
            <ShakeHandsIcon class="icon" />
          </ElIcon>
          <p class="footer-text">Savjetovanje</p>
        </ElCol>
        <ElCol
          :xs="24"
          :sm="12"
          :md="6"
          align="center"
          class="widget-wrapper"
          v-motion-slide-bottom
          :duration="1000"
          :delay="750"
        >
          <ElIcon class="icon-wrapper">
            <DocumentIcon class="icon" />
          </ElIcon>
          <p class="footer-text">Dokumentacija</p>
        </ElCol>
      </ElRow>

      <ElRow style="margin-top: 32px" v-motion-slide-top :duration="1000" :delay="1000">
        <ElCol :xs="24" :sm="8">
          <ElRow class="footer-text details-wrapper-left">House of Cheetah</ElRow>
          <ElRow class="footer-text details-wrapper-left">Radnička 22b</ElRow>
          <ElRow class="footer-text details-wrapper-left">10340 Vrbovec</ElRow>
          <ElRow class="footer-text details-wrapper-left">Hrvatska</ElRow>
        </ElCol>
        <ElCol :xs="24" :sm="8" align="center">
          <ElIcon class="logo-wrapper">
            <LogoIcon class="logo" />
          </ElIcon>
        </ElCol>
        <ElCol :xs="24" :sm="8">
          <ElRow class="footer-text details-wrapper-right">
            <a href="tel:+385916049331">+385 91 6049 331</a>
          </ElRow>
          <ElRow class="footer-text details-wrapper-right">
            <a href="mailto:dorothea.py@gmail.com">dorothea.py@gmail.com</a>
          </ElRow>
        </ElCol>
      </ElRow>

      <ElRow justify="center" align="middle" v-motion-slide-top :duration="1000" :delay="1200">
        <a href="/policy" class="footer-text">Politika web stranice</a>
      </ElRow>

      <ElRow justify="center" class="ending-line" v-motion-slide-top :duration="1000" :delay="1500">
        <p class="footer-text">
          Copyright © 2025 House of Cheetah.
          <a href="https://innova-tech.hr/" target="_blank" style="font-weight: 600">
            Web stranicu izradio InnovaTech
          </a>
        </p>
      </ElRow>
    </template>
  </footer>
</template>

<style scoped>
footer {
  padding: 32px;
  background-color: rgba(64, 63, 69, 0.85);
  border-top-left-radius: 8px;
  border-top-right-radius: 8px;
}
.widget-wrapper {
  padding: 20px;
  color: var(--el-color-primary);
}
.icon-wrapper {
  background-color: var(--el-color-primary);
  border-radius: 100%;
  padding: 10px;
  width: 80px;
  height: 80px;
}
.icon {
  color: #063f74;
  padding: 4px;
  width: 80px;
  height: 80px;
}
a {
  color: var(--el-color-primary);
}
.footer-text {
  font-size: 16px;
  letter-spacing: 0.3px;
  color: var(--el-color-primary);
}
.details-wrapper-left {
  justify-content: start;
  margin-left: 20%;
}
.details-wrapper-right {
  justify-content: end;
  margin-right: 20%;
}
.logo-wrapper {
  width: 180px;
  height: auto;
  padding: 20px;
}
.logo {
  width: 180px;
  height: auto;
  color: var(--el-color-primary);
}
.media-icon-wrapper {
  margin: 8px 16px;
  width: 40px;
  height: 40px;
}
.media-icon {
  width: 40px;
  height: 40px;
}
.ending-line {
  margin-top: 16px;
  text-align: center;
}

@media (max-width: 768px) {
  .details-wrapper-left {
    justify-content: center;
    margin-left: 0;
  }
  .details-wrapper-right {
    justify-content: center;
    margin-right: 0;
  }
}

@media only screen and (max-width: 991px) {
  footer {
    padding: 5%;
  }
}
</style>
