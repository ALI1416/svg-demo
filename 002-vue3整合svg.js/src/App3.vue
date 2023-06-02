<script setup>
import {Rect, SVG} from '@svgdotjs/svg.js'
import {onMounted} from "vue"

onMounted(() => {
  /* 其他元素 */
  const draw = SVG().addTo('body')
  draw.rect(10, 10)
  // 新建矩形，等同于以上
  new Rect().size(10, 10).move(20, 20).addTo(draw)
  // 传入属性
  draw.rect({width: 10, height: 10, x: 40, y: 40})
  new Rect({width: 10, height: 10, x: 60, y: 60}).addTo(draw)
  // 新建指定属性
  draw.element("title", {id: "title"}).words("标题")

  /* 矩形 */
  const draw2 = SVG().addTo('body')
  // 普通矩形
  draw2.rect(50, 50)
  // 圆角矩形
  draw2.rect(50, 50).radius(20).move(100, 100)
  // 不等圆角矩形
  draw2.rect(50, 50).radius(10, 20).move(200, 200)

  /* 圆 */
  const draw3 = SVG().addTo('body')
  // 指定直径的圆
  draw3.circle(50)
  // 指定半径的圆
  draw3.circle().radius(10).move(100, 100)

  /* 椭圆 */
  const draw4 = SVG().addTo('body')
  // 指定直径的椭圆
  draw4.ellipse(50, 100)
  // 指定半径的椭圆
  draw4.ellipse().radius(10, 20).move(100, 100)

  /* 直线 */
  const draw5 = SVG().addTo('body')
  // 划线
  const line = draw5.line(0, 0, 100, 150).stroke({width: 2, color: 'black'})
  // 打印数组
  console.log(line.array())
  // 更新
  // line.plot(50, 30, 100, 150)
  // line.plot('0,0 100,150')
  // line.plot([0, 0, 100, 150])
  line.plot([[0, 0], [100, 150]])

  /* 多线段 */
  const draw6 = SVG().addTo('body')
  // 划线
  const polyline = draw6.polyline('0,0 100,50 50,100').stroke({width: 2, color: 'black'})
  // 打印数组
  console.log(polyline.array())
  // 更新
  // polyline.plot('0,0 100,50 50,100 150,50 200,50')
  // polyline.plot([0, 0, 100, 50, 50, 100, 150, 50, 200, 50])
  polyline.plot([[0, 0], [100, 50], [50, 100], [150, 50], [200, 50]])
  // 清空缓存
  polyline.clear();

  /* 多边形 */
  const draw7 = SVG().addTo('body')
  // 划多边形
  const polygon = draw7.polygon('0,0 100,50 50,100').stroke({width: 2, color: 'black'})
  // 打印数组
  console.log(polygon.array())
  // 更新
  // polygon.plot('0,0 100,50 50,100 150,50 200,50')
  // polygon.plot([0, 0, 100, 50, 50, 100, 150, 50, 200, 50])
  polygon.plot([[0, 0], [100, 50], [50, 100], [150, 50], [200, 50]])
  // 清空缓存
  polygon.clear();

  /* 路径 */
  const draw8 = SVG().addTo('body')
  const path = draw8.path('M0 0 H50 A20 20 0 1 0 100 50 v25 C50 125 0 85 0 85 z')
  // 打印数组
  console.log(path.array())
  // 获取路径总长度
  console.log(path.length())
  // 获取指定路径长度的点坐标
  console.log(path.pointAt(105))
  // 更新
  path.plot('M10 80 C 40 10, 65 10, 95 80 S 150 150, 180 80')
  // 文本环绕
  path.text('SVG.js rocks!')
  // 清空缓存
  path.clear();
});

</script>

<template>
</template>
