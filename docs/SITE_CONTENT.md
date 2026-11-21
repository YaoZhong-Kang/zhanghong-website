# 张弘网站：内容维护说明

当前站点使用 al-folio，发布地址为 <https://yaozhong-kang.github.io/zhanghong-website/>。

## 两个模板版本

| 版本                 | 源码分支   | 访问地址                                                      |
| -------------------- | ---------- | ------------------------------------------------------------- |
| al-folio             | `main`     | <https://yaozhong-kang.github.io/zhanghong-website/>          |
| HugoBlox Academic CV | `hugoblox` | <https://yaozhong-kang.github.io/zhanghong-website/hugoblox/> |

两个版本使用相同的官方教师资料，分别编辑、分别构建。HugoBlox 的内容维护方法见该分支的 `README.md`。`gh-pages` 保存自动生成的发布文件，不直接编辑它。

两份发布工作流共用同一并发组，al-folio 发布步骤保护 `/hugoblox/` 目录；修改发布流程时请保留这两项设置。

发布工作流同时在 `gh-pages` 根目录生成 `.nojekyll`。两个版本都已在 Actions 中构建完成，此文件让 Pages 直接提供生成文件，避免再次经过 Jekyll 时忽略 Hugo 以 `_entry` 开头的样式文件。请保留该步骤；仅在 `hugoblox/` 子目录放置 `.nojekyll` 不能代替根目录标记。

## 本轮资料来源

- [上海大学理学院物理系教师介绍](https://physics.shu.edu.cn/info/1082/1559.htm)：正文更新于2022年9月21日，页面发布于2022年9月22日。用于职称、导师资格、研究方向、课程和联系方式。
- [上海大学理学院教师介绍](https://scicol.shu.edu.cn/szdw/faculty/zh.htm)：更新于2021年6月16日。用于教育和任职的精确年月、代表性科研项目，并补充一篇2016年论文。
- 论文作者、DOI 和 arXiv 编号核对自各论文的 arXiv 记录；保留原论文中的 Kilar Zhang / Hong Zhang 署名。
- 头像使用理学院原图：<https://scicol.shu.edu.cn/__local/9/33/1D/48DD79DD2DD92BBD02DBF45167D_1A980C46_A39A.jpg>。保存为 `assets/img/profile/zhang-hong.jpg`，479×670，原始 JPEG。

两份页面合并后有六篇代表性论文。页面中的资料年份指原始资料的更新时间，不能理解成完整履历或论文已核对到当前年份。

## 改哪里

| 内容                                 | 文件                                                                       |
| ------------------------------------ | -------------------------------------------------------------------------- |
| 网站名称、介绍、语言、网址和页面开关 | `_config.yml`                                                              |
| 首页简介、研究概览、联系信息         | `_pages/about.md`                                                          |
| 头像                                 | `assets/img/profile/zhang-hong.jpg`，文件名在首页的 `profile.image` 中指定 |
| 研究方向与历史科研项目               | `_pages/research.md`                                                       |
| 论文页面导语                         | `_pages/publications.md`                                                   |
| 论文条目与首页精选                   | `_bibliography/papers.bib`                                                 |
| 简历数据                             | `_data/cv.yml`                                                             |
| 简历页面的中文排版                   | `_pages/cv.md`                                                             |
| JSON 格式的简历副本                  | `assets/json/resume.json`                                                  |
| 课程                                 | `_pages/teaching.md`                                                       |
| 邮箱、INSPIRE 图标链接               | `_data/socials.yml`                                                        |

## 在 GitHub 上修改一处文字

1. 打开仓库的 **Code** 页面，确认分支为 `main`。
2. 按上表找到文件，点击编辑按钮。Markdown 文件开头两条 `---` 之间是配置，正文在第二条 `---` 之后。
3. 完成修改后点击 **Commit changes**，填写能说明修改内容的提交消息。
4. 打开 **Actions → Deploy site**，查看新提交的运行结果。构建成功后，再确认 **pages build and deployment** 完成。
5. 刷新网站，核对文字、图片和链接。此站的项目路径是 `/zhanghong-website`，内部链接沿用 `relative_url` 写法。

## 添加论文

在 `papers.bib` 增加一条 BibTeX。保留真实作者、标题、期刊、年份、DOI 和 arXiv 编号。

- `selected = {true}`：出现在首页精选列表。
- `bibtex_show = {true}`：显示 BibTeX 按钮。
- `arxiv` 只填编号，例如 `2002.10961`。
- 不要复制旧条目的奖项、引用次数、缩略图或社交链接到新论文。
- `_config.yml` 中的作者高亮同时匹配 Kilar Zhang 与 Hong Zhang。

## 后续扩展栏目

课题组成员、新闻、AI 小游戏和主办会议尚无已提供的具体资料，因此暂不发布。模板的演示文章、人员、课程和项目仍留在源代码历史与文件中，但通过 `exclude` 和 `published: false` 排除，不能直接恢复整个示例集合来开通栏目。

补充新内容时先填写真实资料，再启用对应页面；新增游戏或会议页可采用普通 `layout: page`。确有服务器或 AI API 需求的游戏需要另行设计服务端。

本轮没有提供可下载的正式简历 PDF。`Render a CV` 工作流保留为手动运行，确认中文 PDF 的内容、字体和版式后，再恢复自动生成，并设置实际下载路径。当前 `assets/rendercv/` 不参与站点发布。

模板附带的 `Lighthouse Badger` 徽章发布也改为手动运行；站点地址与分支已对应本站，后续确有需要时再配置其专用令牌。它不参与网站的构建与发布。

## 检查

修改后检查首页、导航、论文、简历和教学页。格式检查使用 `npm run lint:prettier`；页面构建由现有 `Deploy site` 工作流执行。不要将上游文档中的 `/al-folio` 路径写回本站配置。
