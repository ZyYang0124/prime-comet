# 河北大学蛛形学研究室网站 (Arachnology Lab in HBU)

研究室官方网站，线上地址：<https://hbuara.com/>

基于 [Hugo](https://gohugo.io/) 与 [HugoBlox (Wowchemy) Research Group 模板](https://github.com/HugoBlox/hugo-blox-builder)搭建，通过 Hugo Modules 引入主题，无需手动维护主题代码。

## 技术栈

| 组件 | 版本 / 说明 |
|---|---|
| Hugo | **0.135.0 extended**（Netlify 与 GitHub Actions 中均已锁定，请勿随意升级） |
| Go | Hugo Modules 依赖，本地构建前需安装（建议 1.18+） |
| 主题 | `blox-bootstrap/v5`（见 `go.mod` 与 `config/_default/module.yaml`） |
| 部署 | push 到 `main` 分支 → GitHub Actions 自动构建 → GitHub Pages；另保留 `netlify.toml` 可用 Netlify 部署 |

## 本地开发

```bash
# 首次运行会自动下载主题模块（需要已安装 Go）
hugo server

# 本地完整构建（产物输出到 public/，已加入 .gitignore）
hugo --gc --minify
```

本地预览地址默认为 <http://localhost:1313/>。

## 目录结构

```
├── config/_default/        # 站点配置（YAML）
│   ├── hugo.yaml           # 站点名、URL、permalink、输出格式等
│   ├── params.yaml         # 外观、导航栏、页脚、搜索、CMS 等参数
│   ├── menus.yaml          # 主导航菜单
│   ├── languages.yaml      # 语言配置（当前仅英文）
│   └── module.yaml         # Hugo Modules 主题引入
├── content/
│   ├── _index.md           # 首页（hero + 研究方向板块 + 全宽背景图）
│   ├── tour/               # 研究方向轮播页（slider）
│   ├── post/               # News 动态，每篇一个文件夹（page bundle）
│   ├── authors/            # 成员档案，每人一个文件夹
│   ├── people/             # 团队页（拉取 authors 档案 + 手工维护的毕业生名单）
│   ├── fieldtrip/          # 野外采集照片墙
│   ├── publication/        # 论文列表（手工维护的引用）
│   ├── contact/            # 联系页
│   └── admin/              # Decap CMS 入口（默认未启用 local backend）
├── assets/media/           # 首页、轮播页等引用的图片
├── assets/scss/            # 自定义样式（template.scss）
├── static/images/          # 野外照片等静态图片
├── static/media/           # 站点 logo
└── .github/workflows/      # 部署工作流（publish.yaml）
```

## 常见维护任务

### 发布新闻（News）

在 `content/post/` 下新建文件夹，命名建议 `YY-主题`（如 `26-spartaeus-genome`），内含：

- `_index.md`：front matter 需 `title`、`subtitle`（期刊名）、`summary`、`authors`（对应 `content/authors/` 下的 slug）、`date`，正文写在 front matter 之后；
- `featured.jpg`（可选）：列表页封面图。

### 更新论文列表（Publications)

编辑 `content/publication/_index.md`：按年份分节（`### 2026`），新论文插到对应年份的最上方，使用 Chicago 格式；本室成员姓名用 `**加粗**`。该页面为纯手工维护，未使用 HugoBlox 的 publication 系统。

### 更新成员（People）

- 在职/新成员：在 `content/authors/<拼音slug>/` 下新建 `_index.md`（可参考 `authors/zhiyongyang/_index.md`），并附 `avatar.jpg`。关键 front matter：`role`、`education`、`social`、`user_groups`（须为 `people/index.md` 中列出的分组之一：Founders / Principal Investigator / Researchers / Students / Graduated students）、`weight`（控制组内排序）。
- 毕业生名单：手工编辑 `content/people/index.md` 底部的 markdown 列表（按毕业年份分节）。

### 添加野外照片（Field Trip）

1. 图片放入 `static/images/fieldtrip/<行程文件夹>/N.jpg`（1.jpg、2.jpg … 依次编号）；
2. 在 `content/fieldtrip/_index.md` 顶部（最新行程在最上）照现有格式添加一节：`## YYYY.MM 地点`、成员名单，以及一个 `<div class="gallery">` 块，`data-fancybox` 属性取一个本次行程独有的组名；
3. 提交前压缩大图（历史上曾因单文件超过 25 MB 导致部署失败）。

### 修改首页 / 研究方向 / 导航

- 首页板块：`content/_index.md`（HugoBlox page builder 的 block 结构）；
- 研究方向轮播：`content/tour/index.md`（slider slides，图片在 `assets/media/`）；
- 导航菜单：`config/_default/menus.yaml`；
- 全站参数（logo、页脚、搜索等）：`config/_default/params.yaml`。

## 部署

推送到 `main` 分支即自动触发 `.github/workflows/publish.yaml` 构建，并由 GitHub Pages 发布。若需 Netlify，`netlify.toml` 已配置好（Hugo 0.135.0 + 缓存插件）。

## 相关链接

- 主题文档：<https://docs.hugoblox.com/>
- Hugo 文档：<https://gohugo.io/documentation/>
