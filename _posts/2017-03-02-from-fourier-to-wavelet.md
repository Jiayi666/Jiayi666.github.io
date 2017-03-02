---
layout:     post
title:      "从傅立叶到小波"
subtitle:   "小波变换与Mallat算法"
date:       2017-03-02
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	True
tags:
    - Wavelet
---

### Integral Fourier Transform
　　积分傅里叶变换，也就是我们在信号分析领域最常用的傅立叶变换形式。

![img](\img\in-post\FT_to_WT\intergral.jpg)

　　但是这种变换方式有一个问题，那就是“缺少时间分辨度”，频率轴上的任意一点都代表了整个时间轴的特性，从而无法具体观察某个时间点的频率分布情况。

### Windowed Fourier Transform / Gabor Transform
　　为了解决上述问题，人们想了一个办法，在希望研究的时间点附近给“信号”加一个窗口函数，这样虽然积分傅立叶变换还是涉及了整个时间轴，但只有窗口函数内部的值不为0。

![img](\img\in-post\FT_to_WT\gabor.jpg)

### Short time Fourier Transform
　　短时傅立叶变换与上述的Gabor变换并无本质差别，而是在对变换核与目标函数之间换了一种认识方法。Gabor变换中我们认为窗函数加载在目标函数上，是对目标函数进行了截取。但同样的，我们也可人将窗口函数看作是“加载在傅立叶变换核函数上”，这样就相当于我们得到了一个可以分析一定时间窗口信息的新变换核。

　　由于公式和Gabor变换一致，就不再赘述。

### Integral Wavelet Transform
　　受到上述短时傅立叶变换的启发，人们直接提出了一个全新的变换核，用来完成能自适应分辨率的函数变换工作。

![img](\img\in-post\FT_to_WT\iwt.jpg)

　　当然，所有上述的积分变换的目标函数都要满足在L2(R)空间内平方可积的条件。如果我们将变换核看作是：

![img](\img\in-post\FT_to_WT\core.jpg)

　　IWT有一些非常重要的特性。由于IWT的变换核也满足平方可积条件，所以不妨设其在时间域的函数存在一个中点`t*`以及一个半径`ΔΨ`，那么上述变换核所对应的时间窗口范围是：

![img](\img\in-post\FT_to_WT\timeW.jpg)

　　相应的，如果对该变换核进行“傅立叶变换”，由于该变换核能量有限，故在频率域也必然满足平方可积条件，可以假设该函数在频域有中点`w*`和半径`ΔΨ^`，由于“从时域和频域开始”对目标函数进行函数变换到(a,b)域是等价的，如下式所示

![img](\img\in-post\FT_to_WT\wab.jpg)

　　其中`η`函数是`Ψ`函数的傅立叶变换结果。

　　所以使用该变换核的函数变换等价于在傅立叶频域中存在着一个窗口，其范围是：

![img](\img\in-post\FT_to_WT\freqW.jpg)

　　可以注意到上述窗口范围存在着特殊的关系，即：

![img](\img\in-post\FT_to_WT\autoadjust.jpg)

　　由于函数中心`w*`与半径`ΔΨ^`与(a,b)无关，是随着变换核确定的**常数**，所以上式就体现出了小波变换的**自适应能力**。在低频区域窗口带宽小，频率分辨率高；在高频区域窗口带宽大，时间分辨率高。

　　由于上述时域与频域两个窗口的存在，变换以后每个(a,b)都对应了原函数时域和频域上**窗口相交**部分的信息。

### Discrete Wavelet Transform