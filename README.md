# 张弘 · 上海大学｜HugoBlox Academic CV 版本

这份网站使用真正的 HugoBlox Academic CV 模板，与同一仓库 `main` 分支的 al-folio 版本并行，便于比较版式和维护方式。

- **HugoBlox 预览**：<https://yaozhong-kang.github.io/zhanghong-website/hugoblox/>
- **al-folio 版本**：<https://yaozhong-kang.github.io/zhanghong-website/>
- **本版本源码分支**：`hugoblox`
- **自动发布文件**：`gh-pages/hugoblox/`，不直接编辑。

## 已采用的资料

姓名、简介、职称、导师身份、联系方式、研究方向、教育工作经历、科研项目、课程和六篇代表性论文，均依据此前核实的上海大学官方介绍整理：

1. [上海大学理学院物理系教师介绍](https://physics.shu.edu.cn/info/1082/1559.htm)：正文更新于2022年9月21日，页面发布于2022年9月22日。
2. [上海大学理学院教师介绍](https://scicol.shu.edu.cn/szdw/faculty/zh.htm)：更新于2021年6月16日。

头像来自理学院页面的原始图片，保存为 `assets/media/authors/me.jpg`。论文作者、DOI 与 arXiv 编号沿用已核实的 al-folio 书目；保留 Kilar Zhang / Hong Zhang 的实际署名。

资料出处与原始更新时间仅在本维护说明中记录。公开页面使用简洁的学术主页文案，不展示资料整理过程、来源页面的更新时间或“最近更新”提示；页脚保留简短的照片来源链接和 HugoBlox 框架署名。学历、工作和项目的真实年月，以及论文发表年份，继续正常显示。

没有可用资料的课题组成员、新闻、AI 小游戏和主办会议暂不发布；模板中的示例人物、项目、课程、文章和 PDF 已移除。

## 内容维护

| 要修改的内容 | 文件 |
| --- | --- |
| 首页的区块、顺序、标题 | `content/_index.md` |
| 老师简介、身份、研究兴趣、主页学历 | `data/authors/me.yaml` |
| 老师头像 | `assets/media/authors/me.jpg` |
| 研究方向和科研项目 | `content/research/index.md` |
| 完整简历与精确年月 | `content/cv/index.md` |
| 教学课程 | `content/teaching/index.md` |
| 论文栏目说明 | `content/publications/_index.md` |
| 每篇论文的元数据与正文 | `content/publications/<论文目录>/index.md` |
| 每篇论文的标准引用 | 同目录的 `cite.bib` |
| 中文导航 | `config/_default/menus.yaml` |
| 品牌、配色、页脚、搜索等 | `config/_default/params.yaml` |
| 站点地址与默认语言 | `config/_default/hugo.yaml` |

在 GitHub 的分支选择器切到 **hugoblox** 后编辑上述文件，再提交修改。新的提交会触发 **Deploy HugoBlox preview**。`main` 分支仍维护 al-folio，不要将两套目录混在一起。

### 论文年份

目前只核实了论文的期刊发表年份。Hugo 需要完整日期用来排序，因此论文元数据的 `date` 使用对应年份的 `01-01` 作为内部排序键，同时保存 `publication_year` 和 `publication_date_precision: year`。它不代表已核实的发表月日。

论文发表日期格式统一为 `2006`（只显示年份）。不要在未补充来源前改成显示月日的格式。`content/publications/_index.md` 通过 `cascade.params.show_date_updated: false` 隐藏原生的“最近更新”提示，不修改或隐藏论文的发表年份。个人履历继续使用精确年月表格；主页学历卡省略日期。

## 本地构建

模板来源：[HugoBlox/hugo-theme-academic-cv](https://github.com/HugoBlox/hugo-theme-academic-cv)，基准提交 `487c67587356a61ba0353ddc95989eab73d21fe8`。

当前固定使用：

- Hugo **Extended 0.162.1**。
- Node.js **22**（CI）。
- pnpm **10.14.0**。
- Go **1.27.4**（CI）。
- HugoBlox Blox 模块：`v0.0.0-20260527025321-61f41d3667f1`。

```bash
pnpm install --frozen-lockfile
hugo server --disableFastRender
```

生产构建及搜索索引：

```bash
hugo --gc --minify --baseURL "https://yaozhong-kang.github.io/zhanghong-website/hugoblox/"
pnpm run pagefind
```

使用模板的原生 `resume-biography-3`、`focus-areas`、`content-collection` 和 `markdown` 区块。无需开通 Ownable 或付费功能。保留 HugoBlox 的框架署名和上游 MIT 许可证。

## 两个版本并行发布的约定

Hugo 工作流只监听 `hugoblox` 分支，将 `public/` 发布到 `gh-pages` 的 `hugoblox/` 子目录。al-folio 工作流保护该目录；两边共用 `zhanghong-gh-pages-publish` 并发组，避免相互覆盖。

仓库 Pages 的发布来源继续使用 `gh-pages / (root)`。不要将此模板默认的整站 `deploy-pages` 工作流恢复回来。

站内导航使用 `cv/`、`research/` 这样的相对路径，避免 `/cv/` 跳到域名根目录。以后选定正式版本并绑定老师自己的域名时，再一起调整 `baseURL` 和发布目标。
