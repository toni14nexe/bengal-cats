<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import IntroductionText from '@/components/shared/IntroductionText.vue'

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
  <main>
    <IntroductionText
      title="House of Cheetah"
      text="Bengalci i djeca – savršeni mali tim."
      text2="U našoj uzgajivačnici House of Cheetah mačići odrastaju u okruženju punom ljubavi, igre i društva. Svakodnevno su okruženi našom djecom i drugim mačkama, što im daje izuzetnu stabilnost i sigurnost u karakteru."
      button-text="KONTAKT"
      button-src="/contact"
    />

    <div ref="containerRef" class="background-container">
      <ElRow v-if="isVisible">
        <ElCol :xs="1" :sm="4" />
        <ElCol :xs="22" :sm="7">
          <h2 v-motion-slide-top :duration="1500" :delay="300">
            Bengalci prirodno obožavaju djecu — vole njihovu energiju, zanimljivost i nježnost. Naši
            mali leopardčići od prvih dana uče:
          </h2>
          <ul v-motion-slide-right :duration="1500" :delay="600" class="mt-12">
            <li><p>igrati se s djecom nježno i pažljivo</p></li>
            <li><p>spavati uz njih i tražiti društvo</p></li>
            <li><p>pratiti ih gdje god idu (jer naravno, „zašto bi ostali sami?“)</p></li>
            <li><p>dijeliti prostor s drugim mačkama bez stresa</p></li>
          </ul>
          <div
            style="background-image: url('/images/left.jpeg')"
            class="image image-left"
            v-motion-slide-bottom
            :duration="1500"
            :delay="900"
          />
        </ElCol>
        <ElCol :span="1" class="hidden-sm-and-up" />
        <ElCol :xs="1" :sm="1" />
        <ElCol :xs="22" :sm="7">
          <div
            style="background-image: url('/images/right.jpeg')"
            class="image image-right"
            v-motion-slide-top
            :duration="1500"
            :delay="900"
          />
          <h2 v-motion-slide-left :duration="1500" :delay="300">
            Lucky, Sansa i Rhaenyra najbolji su dokaz toga — gdje su naša dva dječaka, tu su i oni.
            Bilo da je riječ o igri, maženju, spavanju ili samo “kontroli situacije”, naši bengalci
            uvijek su dio ekipe.
          </h2>
          <p v-motion-slide-bottom :duration="1500" :delay="600" class="mt-12">
            Zahvaljujući takvom okruženju, mačići koji odlaze u nove domove odlaze:
          </p>
          <ul v-motion-slide-right :duration="1500" :delay="600">
            <li><p>odlično socijalizirani</p></li>
            <li><p>naviknuti na djecu i buku doma</p></li>
            <li><p>puni samopouzdanja</p></li>
            <li><p>mazni, razigrani i jako povezani s ljudima</p></li>
          </ul>
          <p v-motion-slide-left :duration="1500" :delay="600" class="mt-12">
            Takav start u životu stvara savršene obiteljske ljubimce s prekrasnim karakterom.
          </p>
        </ElCol>
      </ElRow>
    </div>
  </main>
</template>

<style scoped>
.background-container {
  background-color: rgba(64, 63, 69, 0.85);
  padding: 64px 0;
  min-height: 100dvh;
}
h2 {
  font-weight: 700;
  text-underline-offset: 20px;
  letter-spacing: 1px;
  color: var(--el-color-primary);
}
p {
  font-size: 20px;
  letter-spacing: 1.2px;
  max-width: 350px;
  text-align: center;
  color: white;
  text-align: left;
  padding: 2px !important;
}
li {
  color: white;
}
.image {
  height: 500px;
  background-size: cover;
  background-position: center center;
  background-repeat: no-repeat;
  margin: 24px 0;
  border-radius: 8px;
}
.image-right {
  background-position: center center;
}

@media only screen and (max-width: 768px) {
  h1 {
    font-size: 24px;
  }
  p {
    font-size: 14px;
    padding: 16px;
  }
}
</style>
