<script setup lang="ts">
import PageTitle from '@/components/shared/PageTitle.vue'
import { ref, onMounted } from 'vue'
import { ArrowLeftBold, ArrowRightBold } from '@element-plus/icons-vue'

type GalleryJsonResponse = {
  kittens: string[]
  females: string[]
  males: string[]
}

const dialog = ref({ isOpen: false, imageUrl: '' })
const allImages = ref<GalleryJsonResponse>({
  kittens: [],
  females: [],
  males: [],
})
const categoryImages = ref([])
const activeTab = ref<'kittens' | 'females' | 'males'>('kittens')

onMounted(async () => {
  try {
    const res = await fetch('/gallery/gallery.json')
    allImages.value = await res.json()
    categoryImages.value = allImages.value.kittens
  } catch (err) {
    console.error('Gallery loading error:', err)
  }
})

function handleTabChange(tabData) {
  if (tabData.props.name === 'males') categoryImages.value = allImages.value.males
  else if (tabData.props.name === 'females') categoryImages.value = allImages.value.females
  else categoryImages.value = allImages.value.kittens
}

function openDialog(imageUrl) {
  dialog.value = {
    isOpen: true,
    imageUrl: imageUrl,
  }
}

function switchToPrevImage() {
  const currentIndex = categoryImages.value.indexOf(dialog.value.imageUrl)
  const prevIndex = currentIndex === 0 ? categoryImages.value.length - 1 : currentIndex - 1
  dialog.value.imageUrl = categoryImages.value[prevIndex]
}

function switchToNextImage() {
  const currentIndex = categoryImages.value.indexOf(dialog.value.imageUrl)
  const nextIndex = currentIndex === categoryImages.value.length - 1 ? 0 : currentIndex + 1
  dialog.value.imageUrl = categoryImages.value[nextIndex]
}
</script>

<template>
  <main style="max-width: 90%; margin: auto">
    <PageTitle title="GALERIJA" />

    <ElTabs v-model="activeTab" @tab-click="handleTabChange" stretch>
      <ElTabPane label="MAČIĆI" name="kittens">
        <div
          v-if="activeTab === 'kittens'"
          class="images-container"
          v-motion-slide-bottom
          :duration="1500"
        >
          <ElRow :gutter="20" justify="center" class="gallery-container">
            <ElCol
              v-if="categoryImages.length"
              v-for="(src, index) in categoryImages"
              :key="index"
              :xs="24"
              :sm="12"
              :md="8"
              :lg="6"
              align="center"
            >
              <img
                :src="`/gallery/${src}`"
                alt="Gallery image"
                class="gallery-image"
                @click="openDialog(src)"
              />
            </ElCol>
            <p v-else class="no-images-text">Trenutno nema dostupnih slika!</p>
          </ElRow>
        </div>
      </ElTabPane>
      <ElTabPane label="ŽENKE" name="females">
        <div
          v-if="activeTab === 'females'"
          class="images-container"
          v-motion-slide-bottom
          :duration="1500"
        >
          <ElRow :gutter="20" justify="center" class="gallery-container">
            <ElCol
              v-if="categoryImages.length"
              v-for="(src, index) in categoryImages"
              :key="index"
              :xs="24"
              :sm="12"
              :md="8"
              :lg="6"
              align="center"
            >
              <img
                :src="`/gallery/${src}`"
                alt="Gallery image"
                class="gallery-image"
                @click="openDialog(src)"
              />
            </ElCol>
            <p v-else class="no-images-text">Trenutno nema dostupnih slika!</p>
          </ElRow>
        </div>
      </ElTabPane>
      <ElTabPane label="MUŽJACI" name="males">
        <div
          v-if="activeTab === 'males'"
          class="images-container"
          v-motion-slide-bottom
          :duration="1500"
        >
          <ElRow :gutter="20" justify="center" class="gallery-container">
            <ElCol
              v-if="categoryImages.length"
              v-for="(src, index) in categoryImages"
              :key="index"
              :xs="24"
              :sm="12"
              :md="8"
              :lg="6"
              align="center"
            >
              <img
                :src="`/gallery/${src}`"
                alt="Gallery image"
                class="gallery-image"
                @click="openDialog(src)"
              />
            </ElCol>
            <p v-else class="no-images-text">Trenutno nema dostupnih slika!</p>
          </ElRow>
        </div>
      </ElTabPane>
    </ElTabs>

    <ElDialog
      v-model="dialog.isOpen"
      fullscreen
      @keyup.left="switchToPrevImage"
      @keyup.right="switchToNextImage"
    >
      <ElRow justify="center" align="middle" style="height: 92dvh">
        <ElCol :xs="0" :sm="1">
          <ElIcon class="gallery-arrow-wrapper" @click="switchToPrevImage">
            <ArrowLeftBold />
          </ElIcon>
        </ElCol>
        <ElCol :xs="24" :sm="22" align="center" style="display: flex">
          <ElIcon
            class="gallery-arrow-wrapper hidden-sm-and-up"
            @click="switchToPrevImage"
            style="left: 5px"
          >
            <ArrowLeftBold />
          </ElIcon>
          <img :src="`/gallery/${dialog.imageUrl}`" alt="Gallery image" style="margin: 0 auto" />
          <ElIcon
            class="gallery-arrow-wrapper hidden-sm-and-up"
            @click="switchToNextImage"
            style="right: 5px"
          >
            <ArrowRightBold />
          </ElIcon>
        </ElCol>
        <ElCol :xs="0" :sm="1" align="end">
          <ElIcon class="gallery-arrow-wrapper" @click="switchToNextImage">
            <ArrowRightBold />
          </ElIcon>
        </ElCol>
      </ElRow>
    </ElDialog>
  </main>
</template>

<style scoped>
.images-container {
  margin-top: 24px;
  margin-bottom: 100px;
}
.gallery-container {
  background-color: rgba(64, 63, 69, 0.85);
  opacity: 0.95;
  border-radius: 24px;
  row-gap: 24px;
  padding: 64px;
}
.gallery-image {
  width: 100%;
  height: 300px !important;
  border-radius: 8px;
  object-fit: cover;
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
  width: 100%;
  height: 100%;
}
.gallery-image:hover {
  transform: scale(1.03);
  cursor: pointer;
}
.gallery-arrow-wrapper {
  background-color: black;
  color: white !important;
  width: 36px !important;
  height: 36px !important;
  border-radius: 100%;
  transition: 0.2s ease-in-out;
}
.gallery-arrow-wrapper:hover {
  background-color: var(--el-color-primary);
  cursor: pointer;
}
.no-images-text {
  color: white;
  font-size: 20px;
  text-align: center;
  padding: 8px;
}

@media only screen and (max-width: 768px) {
  .gallery-container {
    padding: 5%;
  }
  .gallery-arrow-wrapper {
    opacity: 0.5;
    position: absolute !important;
    top: calc(50% - 18px);
  }
  .gallery-arrow-wrapper:hover {
    background-color: black;
  }
}

@media only screen and (max-width: 991px) {
  .review-container {
    height: 230px;
  }
  .review-item {
    margin: 0;
  }
  h1 {
    font-size: 24px;
  }
  p {
    font-size: 14px;
  }
}
</style>
