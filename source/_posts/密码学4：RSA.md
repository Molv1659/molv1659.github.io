---
title: 密码学4：RSA
date: 2021/03/07
photos: http://www.sisicheng.com/cdn/article-covers/7.JPG
categories: 砂糖实验室
avatar: http://www.sisicheng.com/cdn/Kirito1.jpg
authorLink: http://www.sisicheng.com/blog
---
permalink: rsa
目前大家经常看到并容易使用的加密算法就是这个了，之前说的非对称密钥系统中，公钥加密私钥解密，私钥加密公钥解密的特性，想起来就蛮神奇的，好奇怎么实现这一特点的，下面这个视频讲得很清楚，我就不写了23333，直接导过去：

<iframe src="//player.bilibili.com/player.html?aid=74730093&amp;bvid=BV1gE411i7Xr&amp;cid=127832422&amp;page=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true" style="width: 100%; height: 450px; max-width: 100%; align: center; padding: 20px 0 "> </iframe>

顺便也试试网页里嵌入b站视频23333

具体使用RSA可以在这个网站 https://www.devglan.com/online-tools/rsa-encryption-decryption

里面提供了各种功能：

- 生成1024 bit（或其它位数）的私钥公钥：目前破译最高位的就768位，选择位数越大越难分解，安全性越高。
- 加密：选择Public key 或 Private Key，生成**Encrypted Output (Base64)**。
- 解密：选择Public key 或 Private Key，还原出信息
