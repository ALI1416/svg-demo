<script setup>
import {Fragment, SVG} from '@svgdotjs/svg.js'
import {onMounted} from "vue"

onMounted(() => {
  /* 基础元素 */
  const draw = SVG().addTo('body')
  // 新建svg
  const nested = draw.nested()
  nested.rect(10, 10)
  // 新建group
  const group = draw.group()
  group.rect(10, 10).move(20, 20)
  // 新建symbol
  const symbol = draw.symbol()
  symbol.rect(10, 10)
  draw.use(symbol).move(40, 40)
  // 新建defs
  const defs = draw.defs()
  const group2 = defs.group()
  group2.rect(10, 10)
  draw.use(group2).move(60, 60).fill('#9c9').width(15).height(15)
  // 新建超链接
  const link = draw.link("https://www.baidu.com/")
  link.rect(10, 10).move(80, 80).fill('#6cf')
  // 更新
  link.to("https://fanyi.baidu.com/")
  // 设置target
  link.target("_blank")
  // 元素设置超链接
  const rect = draw.rect(10, 10).move(100, 100)
  rect.linkTo("https://www.baidu.com/")
  // 返回该连接
  console.log(rect.linker());
  // 删除
  rect.unlink();
  console.log(rect.linker());
  // 新建片段
  const frag = new Fragment()
  frag.rect(10, 10).move(120, 120)
  frag.circle(10).move(140, 140)
  draw.add(frag)
});
</script>

<template>
</template>
