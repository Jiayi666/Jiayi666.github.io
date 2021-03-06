---
layout:     post
title:      "滤波器组与离散小波变换"
subtitle:   "Introduction to Wavelets and Wavelet Transforms-Ch03"
date:       2016-07-20
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - Wavelet
---

#### 高低阶尺度系数关系

　　由相邻时间尺度上尺度函数的递推公式加上`j`向上的伸缩变换，可以得到对于在第`j+1`阶尺度函数空间中的函数可以展开为：

![img](\img\in-post\Wavelet\3.4.png)

　　上式也可以写作用第`j`阶尺度函数加上小波函数项表达：

![img](\img\in-post\Wavelet\3.6.png)

　　其中如果尺度函数与小波函数规范正交，即可用*内积*的方法求出尺度函数与小波函数系数，可得到如下关系：

![img](\img\in-post\Wavelet\3.9.png)

　　仔细观察可得出上述两式非常类似于**卷积**运算。

#### 下抽样（由细尺度到粗尺度）

　　下抽样就是**隔n抽1**，如果n取2的话：

![img](\img\in-post\Wavelet\F3.1.png)

　　由于**滤波过程就是做卷积**，结合上述`(3.9)`式中所描述的尺度系数间关系呈现卷积运算，可以发现，通过如下方式设计**滤波**系统，可以得到从`j+1`到`j`尺度的**尺度系数转换**：

![img](\img\in-post\Wavelet\F3.2.png)

　　可见上图中从左至右完成了从`Cj+1`到`j`系数的转换。

#### 上抽样（由粗尺度到细尺度）

　　与下抽样相反，上抽样的方法是**在相邻信号中加入n-1个0**，对式`(3.9)`稍作变换，得到从粗尺度向细尺度转换的关系式：

![img](\img\in-post\Wavelet\3.20.png)

　　同样采用滤波的方式，可以得到如下滤波系统图：

![img](\img\in-post\Wavelet\F3.7.png)