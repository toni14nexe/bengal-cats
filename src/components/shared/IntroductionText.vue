<script setup lang="ts">
defineProps<{
  title: string
  text?: string
  text2?: string
  buttonText?: string
  buttonSrc?: string
}>()
</script>

<template>
  <ElRow align="middle" class="introduction-text-container">
    <ElRow style="row-gap: 16px">
      <ElCol v-motion-slide-left :duration="1500" :delay="300" :xs="24" :lg="14">
        <h1 style="color: var(--el-color-primary)">{{ title }}</h1>
      </ElCol>
      <ElCol :xs="0" :lg="10" />
      <ElCol v-if="text || text2" :xs="24" :lg="14">
        <p v-if="text" v-motion-slide-right :duration="1500" :delay="600">
          {{ text }}
        </p>
        <p v-if="text2" v-motion-slide-left :duration="1500" :delay="900" style="margin-top: 16px">
          {{ text2 }}
        </p>
      </ElCol>
      <ElCol :xs="0" :lg="10" />
      <ElCol
        v-if="buttonSrc && buttonText"
        v-motion-slide-bottom
        :xs="24"
        :lg="14"
        :duration="1500"
        :delay="1200"
      >
        <RouterLink :to="`${buttonSrc}`">
          <ElButton size="large">{{ buttonText }}</ElButton>
        </RouterLink>
      </ElCol>
      <ElCol :xs="0" :lg="10" />
    </ElRow>
  </ElRow>
</template>

<style scoped>
.introduction-text-container {
  padding: 120px;
  height: calc(100dvh - 60px);
}
h1 {
  color: white;
}
p {
  color: white;
}
button {
  font-size: large;
}

@media (max-width: 992px) {
  .introduction-text-container {
    padding: 16px;
  }
}
</style>
