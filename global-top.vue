<script setup lang="ts">
import { computed } from 'vue'
import { useNav } from '@slidev/client'
const { currentLayout, currentSlideRoute } = useNav()
const show = computed(() => {
  const fm = (currentSlideRoute.value as any)?.meta?.slide?.frontmatter ?? {}
  return !['hero', 'iframe'].includes(currentLayout.value as string) && fm.footer !== false
})
</script>

<template>
  <div v-if="show" class="absolute right-7 bottom-4 z-50 flex items-center gap-5" style="opacity:.9">
    <img src="/cgs/CGS-Logo-Horizontal-Color.png" style="height:26px" />
    <span style="width:1px;height:22px;background:#C9DEE8"></span>
    <img src="/logos/usgs.svg" style="height:26px" />
    <span style="width:1px;height:22px;background:#C9DEE8"></span>
    <img src="/logos/iow.png" style="height:30px" />
  </div>
</template>
