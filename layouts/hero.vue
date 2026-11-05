<script setup lang="ts">
// Graph motif: water features as nodes, links as edges
const nodes = [
  { n: 'dam', x: 640, y: 60, s: 54 }, { n: 'gage', x: 740, y: 140, s: 50 }, { n: 'reservoir', x: 860, y: 90, s: 54 },
  { n: 'river', x: 900, y: 210, s: 50 }, { n: 'huc', x: 810, y: 290, s: 56 }, { n: 'aquifer', x: 700, y: 250, s: 52 },
  { n: 'gage', x: 710, y: 360, s: 44 }, { n: 'dam', x: 820, y: 420, s: 48 }, { n: 'river', x: 910, y: 380, s: 44 },
]
const edges = [[0,1],[1,2],[2,3],[3,4],[4,5],[5,1],[0,5],[5,6],[4,7],[7,8],[3,8],[6,7]]
</script>

<template>
  <div class="slidev-layout hero h-full w-full relative overflow-hidden">
    <svg class="absolute inset-0 w-full h-full" viewBox="0 0 980 552" preserveAspectRatio="xMidYMid slice" style="opacity:.3">
      <g stroke="#fff" stroke-width="1.8" fill="none">
        <line v-for="(e, i) in edges" :key="i" :x1="nodes[e[0]].x" :y1="nodes[e[0]].y" :x2="nodes[e[1]].x" :y2="nodes[e[1]].y" />
      </g>
      <g v-for="(nd, i) in nodes" :key="'n'+i">
        <circle :cx="nd.x" :cy="nd.y" :r="nd.s * 0.7" fill="#2C84B9" opacity=".55" />
        <WaterIcon :name="nd.n" :size="nd.s" color="#fff" :x="nd.x - nd.s / 2" :y="nd.y - nd.s / 2" />
      </g>
      <path d="M0 470 Q120 430 240 470 T480 470 T720 470 T980 470 V552 H0Z" fill="#fff" opacity=".25"/>
      <path d="M0 505 Q120 470 240 505 T480 505 T720 505 T980 505 V552 H0Z" fill="#fff" opacity=".25"/>
    </svg>
    <div class="relative z-10 px-16 py-12 h-full flex flex-col justify-center"><div style="max-width:62%"><slot /></div></div>
  </div>
</template>
