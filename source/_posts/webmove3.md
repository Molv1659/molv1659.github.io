---
title: 网站第三次搬家
date: 2024/12/15
photos: https://www.sisicheng.com/cdn/article-cover/Frieren.webp
categories: 砂糖实验室
avatar: https://www.sisicheng.com/cdn/kirito1.jpg
authorLink: http://www.sisicheng.com
---
一年又过去了，cloudcone又要续费，每年花20刀，还老因为它的迁移更新把我网站弄坏，每次休的时候都忘完了，折腾半天。今年又把我跑的mongo数据库弄崩了，不想修了。反正动态网页就是个toy project不要也罢，把我hexo网页搞好就成。于是有了这第三次搬家。

目标是搬到github-pages白嫖一下免费的托管，然后自己domain替代一下，甚至不太看得出来是在github上的。

被hexo官网教程给坑大了，根本不用什么建特殊workflow/pages.yml什么的，瞎折腾一上午，最后还是问gpt调好了，记录一下：
- sisicheng.com apex domain add A record to github pages server IPs
- www.sisischeng.com CNAME record to molv1659.github.io
- add source/CNAME file with www.sisicheng.com
- hexo deploy to gh-pages branches
- add npm update cmd that handles git and hexo
- adjust cdn dir
