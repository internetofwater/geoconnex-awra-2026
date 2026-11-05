<script setup lang="ts">
withDefaults(defineProps<{ name: string; size?: number; color?: string; x?: number; y?: number }>(), {
  size: 48,
  color: 'currentColor',
})
</script>

<template>
  <svg
    :x="x" :y="y" :width="size" :height="size" viewBox="0 0 48 48"
    fill="none" stroke="currentColor" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round"
    :style="{ color }"
  >
    <!-- dam -->
    <g v-if="name === 'dam'">
      <path d="M8 8 H40 L36 36 H12 Z" fill="currentColor" fill-opacity=".18" />
      <path d="M18 14 V30 M24 14 V30 M30 14 V30" />
      <path d="M2 42 q4 -3 8 0 t8 0 t8 0 t8 0 t8 0 t8 0" />
    </g>
    <!-- stream gage -->
    <g v-else-if="name === 'gage'">
      <rect x="12" y="3" width="20" height="14" rx="2" fill="currentColor" fill-opacity=".18" />
      <path d="M22 17 V40" stroke-width="4" />
      <path d="M36 14 V40 M33 20 H36 M33 26 H36 M33 32 H36" />
      <path d="M2 34 q5 -4 10 0 t10 0 t10 0 t10 0 t6 0" />
      <path d="M2 42 q5 -4 10 0 t10 0 t10 0 t10 0 t6 0" />
    </g>
    <!-- reservoir / lake -->
    <g v-else-if="name === 'reservoir'">
      <path d="M5 26 C5 14 17 10 25 15 C35 10 44 18 43 29 C41 40 25 43 14 40 C8 38 5 33 5 26Z" fill="currentColor" fill-opacity=".18" />
      <path d="M13 27 q3 -3 6 0 t6 0 t6 0 t6 0" />
    </g>
    <!-- river / mainstem -->
    <g v-else-if="name === 'river'">
      <path d="M12 3 C34 8 12 18 24 25 S38 34 30 45" stroke-width="5" />
      <path d="M42 8 C36 12 32 15 27 20" stroke-width="3" />
      <path d="M5 30 C12 30 16 32 21 33" stroke-width="3" />
    </g>
    <!-- aquifer -->
    <g v-else-if="name === 'aquifer'">
      <path d="M3 10 H45" />
      <path d="M3 18 q10 -5 21 0 t21 0" />
      <path d="M3 28 H45 V44 H3 Z" fill="currentColor" fill-opacity=".22" />
      <path d="M8 36 q4 -3 8 0 t8 0 t8 0 t8 0" />
      <path d="M32 3 V32 M28 3 H36" stroke-width="3" />
    </g>
    <!-- HUC watershed -->
    <g v-else-if="name === 'huc'">
      <path d="M24 3 L40 11 L43 30 L31 45 L11 41 L4 22 Z" fill="currentColor" fill-opacity=".15" />
      <path d="M24 12 V28 L15 38 M24 28 L34 37 M24 19 L15 13 M24 21 L34 14" />
    </g>
    <!-- state / admin boundary -->
    <g v-else-if="name === 'state'">
      <path d="M7 7 H41 V19 H45 V33 L35 45 H20 V37 H7 Z" fill="currentColor" fill-opacity=".15" />
      <circle cx="24" cy="24" r="2.5" fill="currentColor" />
    </g>
    <!-- dataset -->
    <g v-else-if="name === 'dataset'">
      <ellipse cx="24" cy="10" rx="15" ry="6" fill="currentColor" fill-opacity=".18" />
      <path d="M9 10 V37 A15 6 0 0 0 39 37 V10" />
      <path d="M9 23 A15 6 0 0 0 39 23" />
    </g>
    <!-- snow sensor -->
    <g v-else-if="name === 'snow'">
      <path d="M24 4 V44 M7 14 L41 34 M7 34 L41 14" />
      <path d="M19 6 L24 11 L29 6 M19 42 L24 37 L29 42" />
    </g>
    <!-- model -->
    <g v-else-if="name === 'model'">
      <path d="M10 36 L24 10 L38 36 Z" />
      <circle cx="10" cy="36" r="5" fill="currentColor" /><circle cx="24" cy="10" r="5" fill="currentColor" /><circle cx="38" cy="36" r="5" fill="currentColor" />
    </g>
    <!-- url / persistent id -->
    <g v-else-if="name === 'url'">
      <rect x="3" y="8" width="42" height="32" rx="5" fill="currentColor" fill-opacity=".15" />
      <path d="M3 17 H45" />
      <g transform="translate(24 28) scale(.8) translate(-24 -24)">
        <path d="M20 28 L28 20" />
        <path d="M19 23 l-3 3 a4.5 4.5 0 0 0 6.4 6.4 l3 -3" />
        <path d="M29 25 l3 -3 a4.5 4.5 0 0 0 -6.4 -6.4 l-3 3" />
      </g>
    </g>
    <!-- redirect -->
    <g v-else-if="name === 'redirect'">
      <path d="M4 24 H14 C24 24 24 12 36 12 H42 M37 7 L43 12 L37 17" />
      <path d="M14 24 C24 24 24 36 36 36 H42 M37 31 L43 36 L37 41" />
    </g>
    <!-- website / landing page -->
    <g v-else-if="name === 'site'">
      <rect x="4" y="7" width="40" height="34" rx="4" fill="currentColor" fill-opacity=".12" />
      <path d="M4 16 H44" />
      <circle cx="9" cy="11.5" r="1" fill="currentColor" /><circle cx="14" cy="11.5" r="1" fill="currentColor" />
      <rect x="9" y="21" width="13" height="14" rx="2" />
      <path d="M27 22 H39 M27 28 H39 M27 34 H35" />
    </g>
    <!-- code / json-ld -->
    <g v-else-if="name === 'code'">
      <path d="M17 10 C12 10 12 14 12 19 C12 22 9 24 6 24 C9 24 12 26 12 29 C12 34 12 38 17 38" />
      <path d="M31 10 C36 10 36 14 36 19 C36 22 39 24 42 24 C39 24 36 26 36 29 C36 34 36 38 31 38" />
      <path d="M27 14 L21 34" />
    </g>
    <!-- knowledge graph -->
    <g v-else-if="name === 'graph'">
      <path d="M24 25 L10 11 M24 25 L39 9 M24 25 L7 38 M24 25 L41 38 M10 11 L39 9 M7 38 L41 38" />
      <circle cx="24" cy="25" r="6" fill="currentColor" />
      <circle cx="10" cy="11" r="4.5" fill="currentColor" /><circle cx="39" cy="9" r="4.5" fill="currentColor" />
      <circle cx="7" cy="38" r="4.5" fill="currentColor" /><circle cx="41" cy="38" r="4.5" fill="currentColor" />
    </g>
    <!-- person / human -->
    <g v-else-if="name === 'person'">
      <circle cx="24" cy="15" r="8" fill="currentColor" fill-opacity=".18" />
      <path d="M7 43 C7 31 15 27 24 27 S41 31 41 43" fill="currentColor" fill-opacity=".18" />
    </g>
    <!-- AI sparkle -->
    <g v-else-if="name === 'ai'">
      <path d="M20 6 C21 17 27 23 38 24 C27 25 21 31 20 42 C19 31 13 25 2 24 C13 23 19 17 20 6Z" fill="currentColor" fill-opacity=".18" />
      <path d="M38 5 V15 M33 10 H43" />
      <path d="M39 32 V40 M35 36 H43" />
    </g>
    <!-- web map -->
    <g v-else-if="name === 'map'">
      <path d="M4 10 L16 6 L32 10 L44 6 V38 L32 42 L16 38 L4 42 Z" fill="currentColor" fill-opacity=".15" />
      <path d="M16 6 V38 M32 10 V42" />
    </g>
    <!-- dataset submission: person -> dataset -->
    <g v-else-if="name === 'submit'">
      <circle cx="11" cy="15" r="5.5" fill="currentColor" fill-opacity=".18" />
      <path d="M2 38 C2 29 6 25 11 25 S20 29 20 38 Z" fill="currentColor" fill-opacity=".18" />
      <path d="M22 27 H28 M25 23.5 L28.5 27 L25 30.5" />
      <ellipse cx="39" cy="14" rx="8" ry="3.5" fill="currentColor" fill-opacity=".18" />
      <path d="M31 14 V35 A8 3.5 0 0 0 47 35 V14" />
      <path d="M31 24.5 A8 3.5 0 0 0 47 24.5" />
    </g>
  </svg>
</template>
