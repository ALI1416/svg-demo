<script setup>
/* 0、安装并导入依赖 */
// 安装 npm install @svgdotjs/svg.js
import {SVG} from '@svgdotjs/svg.js'
import {onMounted} from "vue"

onMounted(() => {
  /* 追加到body标签尾部 */
  // 1、创建画布(默认尺寸300x300)
  const draw = SVG().addTo('body').size(300, 300)
  // 2、绘制图形
  const rect = draw.rect(100, 100).attr({fill: '#6cf'})
  // 3、导出svg(注意：无法导出动画)
  console.log(draw.svg())
  /* 指定svg */
  const draw1 = SVG("#s1")
  // 原内容不会覆盖
  draw1.rect(100, 100).animate().fill('#6cf').move(100, 100)
  /* 指定group */
  const draw2 = SVG("#g1")
  draw2.rect(10, 10).animate().move(0, 100)
});

</script>

<template>
  <svg id="s1">
    <rect width="100" height="100" fill="#6cf"></rect>
    <defs>
      <g id="g1">
        <rect width="10" height="10"></rect>
      </g>
    </defs>
    <use x="10" y="150" href="#g1"></use>
  </svg>
</template>
