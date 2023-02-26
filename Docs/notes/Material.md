---
id: dceii0itqf54ai3ecx32iyz
title: Material
desc: ''
updated: 1677391841278
created: 1676808003982
---

## 半透明材质与不透明对象生硬交界

一个半透明材质的面片与不透明物体相交，出现生硬的交界：

![HardIntersect](HardIntersect.png)

为避免这个问题，使用一个节点乘上透明度：

![DepthFade](DepthFade.png)

效果：

![Result](Result.png)

但是在从交界线网上是线性均匀地Fade，中间不透明部分和两边半透明部分Fade的程度都是一样的，我们更希望中间不透明部分Fade更慢一点。所以可以根据Alpha值Lerp一下Fade的距离：

![LerpByAlpha](LerpByAlpha.png)

Alpha大的时候，Fade Distance也小，Alpha小的区域，Fade的范围也就越大：

![FadeDistanceLerped](FadeDistanceLerped.png)

## 根据相机距离的透明度衰减

![CameraDepthFade](CameraDepthFade.png)

![](CameraDepthFade_Graph.png)

> :heavy_exclamation_mark:  UE中默认裁剪距离为24  


**Note**