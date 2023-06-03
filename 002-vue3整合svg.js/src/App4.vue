<script setup>
import {SVG} from '@svgdotjs/svg.js'
import {onMounted} from "vue"

onMounted(() => {
  /* 默认文本 */
  const draw = SVG().addTo('body')
  // text的tspan添加文本
  draw.text("Lorem ipsum dolor sit amet consectetur.\nCras sodales imperdiet auctor.").move(0, 20)
  // text添加文本
  draw.plain('Lorem ipsum dolor sit amet consectetur.').move(0, 100)
  /* 自定义文本 */
  const draw2 = SVG().addTo('body')
  draw2.text(function (add) {
    // tspan标签
    add.tspan('Lorem ipsum dolor sit amet ').newLine()
    add.tspan('consectetur').fill('#f06').dy(30)
    add.tspan('.')
    add.tspan('Cras sodales imperdiet auctor.').newLine().dx(20)
    add.newLine('Nunc ultrices lectus at erat')
    add.tspan('dictum pharetra elementum ante').newLine()
  }).move(0, 20)
  /* 文本属性 */
  const draw3 = SVG().addTo('body')
  const text = draw3.text('Some text for you')
  // 定位文本
  text.amove(100, 50)
  // 定位文本x
  text.ax(10)
  // 定位文本y
  text.ay(20)
  // 输出xy
  console.log(text.ax(), text.ay())
  // 输出文本长度
  console.log(text.length())
  const text2 = draw3.text('This is just the start, ').move(0, 30)
  // 启用追加模式
  text2.build(true)
  text2.tspan('something pink in the middle ').fill('#00ff97').newLine()
  text2.plain('and again boring at the end.')
  text2.build(false)
  const text3 = draw3.text('clear').move(0, 30)
  // 清空
  text3.clear();
  /* 字体 */
  const draw4 = SVG().addTo('body')
  const text4 = draw4.text('Font').move(100, 50)
  // 设置字体样式
  text4.font({
    family: 'Helvetica',
    size: 50,
    anchor: 'middle',
    leading: '1.5em'
  })
  // 只设置一个属性
  text4.font('weight', 1000)
  // 获取属性值
  console.log(text.font('leading'))
  /* 路径环绕 */
  const draw5 = SVG().addTo('body')
  const text5 = draw5.text(function (add) {
    add.tspan('We go ')
    add.tspan('up').fill('#f09').dy(-40)
    add.tspan(', then we go down, then up again').dy(40)
  })
  const path = 'M 100 200 C 200 100 300 0 400 100 C 500 200 600 300 700 200 C 800 100 900 100 900 100'
  // 路径环绕
  const textpath = text5.path(path).font({size: 42.5, family: 'Verdana'})
  // 设置属性
  textpath.attr('startOffset', '-5%')
  /* 路径环绕2 */
  const draw6 = SVG().addTo('body')
  const textpath2 = draw6.textPath('Some Text along a path', 'M 100 200 C 200 100 300 0 400 100 C 500 200 600 300 700 200 C 800 100 900 100 900 100')
  // 打印数组
  console.log(textpath2.array())
  // 更新
  textpath2.plot('M 100 200 C 200 100 300 0 400 100')
  // 获取路径
  console.log(textpath2.track())
});
</script>

<template>
</template>
