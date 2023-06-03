<script setup>
import {SVG} from '@svgdotjs/svg.js'
import {onMounted} from "vue"

onMounted(() => {
  /* 图片 */
  const draw = SVG().addTo('body')
  draw.image("../image/苹果.PNG")
  /* 渐变 */
  const draw2 = SVG().addTo('body')
  // 线性渐变
  const linear = draw2.gradient('linear', function (add) {
    add.stop(0, '#333')
    add.stop(1, '#fff')
  })
  const linear2 = draw2.gradient('linear', function (add) {
    add.stop(0, '#333')
    add.stop(1, '#fff')
  }).from(0, 0).to(1, 1)
  // 绑定渐变
  draw2.rect(100, 100).fill(linear)
  draw2.rect(100, 100).move(100, 0).attr({fill: linear2})
  // 获取url
  console.log(linear.url())
  // 径向渐变
  const radial = draw2.gradient('radial', function (add) {
    add.stop({offset: 0, color: '#fff', opacity: 1})
    add.stop({offset: 0.5, color: '#6cf', opacity: 0.5})
    add.stop({offset: 1, color: '#f99', opacity: 1})
  })
  draw2.rect(100, 100).move(0, 100).fill(radial)
  /* 模板 */
  const draw3 = SVG().addTo('body')
  // 绘制模板
  const pattern = draw3.pattern(20, 20, function (add) {
    add.rect(20, 20).fill('#6cf')
    add.rect(10, 10)
    add.rect(10, 10).move(10, 10)
  })
  draw3.rect(100, 100).fill(pattern)
  /* 遮罩 */
  const draw4 = SVG().addTo('body')
  const ellipse = draw4.ellipse(150, 50).move(10, 10).fill('#fff')
  const mask = draw4.mask().add(ellipse)
  const rect = draw4.rect(100, 100)
  rect.maskWith(mask)
  /* 剪切 */
  const draw5 = SVG().addTo('body')
  const ellipse2 = draw5.ellipse(150, 50).move(10, 10).fill('#fff')
  const text = draw5.text('SVG.JS').move(10, 10).font({size: 36})
  const clip = draw5.clip().add(text).add(ellipse2)
  const rect2 = draw5.rect(100, 100)
  rect2.clipWith(clip)
  /* 定义和使用 */
  const draw6 = SVG().addTo('body')
  const rect3 = draw6.rect(10, 10).fill('#f09')
  draw6.use(rect3).move(20, 20)
  const rect4 = draw6.defs().rect(10, 10).fill('#6cf')
  draw6.use(rect4).move(40, 40)
  /* 标记 */
  const draw7 = SVG().addTo('body')
  const path = draw7.path('M0 0 A50 50 0 0 1 50 50 A50 50 0 0 0 100 100')
  path.fill('none').move(20, 20).stroke({width: 1, color: '#ccc'})
  path.marker('start', 10, 10, function (add) {
    add.circle(10).fill('#f06')
  })
  path.marker('mid', 10, 10, function (add) {
    add.rect(5, 10).cx(5).fill('#ccc')
  })
  path.marker('end', 20, 20, function (add) {
    add.circle(6).center(4, 5)
    add.circle(6).center(4, 15)
    add.circle(6).center(12, 10)
    this.fill('#0f9')
  })
  /* 样式 */
  const draw8 = SVG().addTo('body')
  const style = draw8.style('.green', {fill: 'green'})
  style.rule('.blue', {fill: 'blue'})
  draw8.rect(100, 100).attr('class', 'green')
  /* 渲染HTML */
  const draw9 = SVG().addTo('body')
  const foreignObject = draw9.foreignObject(200, 50)
  foreignObject.add(SVG('<input type="text">', true))
});
</script>

<template>
</template>
