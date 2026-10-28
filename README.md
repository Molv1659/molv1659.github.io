# 冬のWorld — 个人博客 (sisicheng.com)

> **这是在维护的博客。** 简历也托管在这里：
> `source/sicheng-wang-resume.pdf` → https://www.sisicheng.com/sicheng-wang-resume.pdf
>
> `~/Code/WebDev/` 里的 `blog/` 和 `SakuraBlog/` 是旧版本，**已弃用、不再维护**。

- Hexo **3.9.0** + Sakura 主题
- 源码仓库：`github.com/Molv1659/blog`（`main` 分支）
- `hexo deploy` 把生成的静态站点推到 `Molv1659/molv1659.github.io` 的 `gh-pages` 分支
- 域名 `www.sisicheng.com`（`source/CNAME`）
- 站点配置见 `_config.yml`（permalink `:year/:title/`，部署目标在最底下）

## Node 版本（重要）

Hexo 3.9 和它的老插件（`hexo-deployer-git@0.2.0` 依赖 `swig`、老版 `uglify-js`）是 2017 年前后的东西，**认准 Node 8**。

```bash
nvm use 8          # v8.17.0，本仓库的 known-good 版本
```

- 本机 nvm 默认已改成 **20**（给别的开发用），所以每次搞博客**先 `nvm use 8`**。
- 实测：Node 20 下 `hexo generate` 虽然报 `INFO 208 files generated`，但生成的**文件全是 0 字节**（Hexo 3.x 在 Node 14+ 上的已知问题，会伴随 `circular dependency` 警告），直接 deploy 就是推一个空站 —— **生成、部署都一定用 Node 8**。
- 没有 `.nvmrc`，版本靠手动切。

## 写文章

```bash
nvm use 8
npx hexo new post "文章标题"        # 生成 source/_posts/文章标题.md + 同名资源文件夹
# 编辑 front-matter：title / date / categories / photos(封面) / avatar / permalink
npx hexo server                    # http://localhost:4000/ 本地预览
npx hexo server --draft            # 预览 source/_drafts/ 里的草稿
```

现有 categories：`砂糖实验室` / `男子大学生の日常` / `戏言` / `影视`。
标题里带 `[` `]` `:` 等 YAML 特殊字符时，`title:` 要加引号。

## 发布

```bash
nvm use 8
npx hexo clean                     # 清掉 public/ 和 db.json 缓存
npx hexo generate                  # 生成静态站点到 public/
npx hexo deploy                    # 推到 molv1659.github.io 的 gh-pages 分支
```

一步到位（`package.json` 里已定义）：

```bash
nvm use 8 && npm run update
# = git add . && git commit -m 'new version' && git push && hexo clean && hexo generate && hexo deploy
```

`npm run update` 先把**源码**提交推到 `Molv1659/blog`，再生成 + 部署静态站到 gh-pages。

### 更新简历

```bash
cp <新简历>.pdf source/sicheng-wang-resume.pdf
nvm use 8 && npx hexo clean && npx hexo generate && npx hexo deploy
```

（`source/sicheng-wang-resume.pdf` 在 git 里是 untracked，但 `hexo generate` 会把它复制进 `public/` 一起部署。）

## 依赖丢了

```bash
nvm use 8 && npm install
```

## 部署前提

- SSH 能推到 `git@github.com:Molv1659/molv1659.github.io.git`
- gh-pages 分支的 GitHub Pages + 自定义域名已配好（`source/CNAME` = `www.sisicheng.com`）
