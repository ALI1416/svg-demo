<script setup>
import {SVG} from '@svgdotjs/svg.js'
import {onMounted} from "vue"

onMounted(() => {
  /* 默认文本 */
  const draw = SVG().addTo('body')
  // text的tspan添加文本
  draw.text("Lorem ipsum dolor sit amet consectetur.\nCras sodales imperdiet auctor.").move(0,20)
  // text添加文本
  draw.plain('Lorem ipsum dolor sit amet consectetur.').move(0,100)
  /* 自定义文本 */
  const draw2 = SVG().addTo('body')
  draw2.text(function(add) {
    add.tspan('Lorem ipsum dolor sit amet ').newLine()
    add.tspan('consectetur').fill('#f06')
    add.tspan('.')
    add.tspan('Cras sodales imperdiet auctor.').newLine().dx(20)
    add.newLine('Nunc ultrices lectus at erat')
    add.tspan('dictum pharetra elementum ante').newLine()
  }).move(0,20)
  /* 文本 */
  const draw3 = SVG().addTo('body')
  const text = draw3.text('Some text for you')
  // 定位文本
  text.amove(100, 50)
  // 定位文本x
  text.ax(10)
  // 定位文本y
  text.ay(20)
  // 输出xy
  console.log(text.ax(),text.ay())
});

</script>

<template>
</template>
