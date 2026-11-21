# 研究方向图片来源

首页和研究方向页共用 `assets/media/research/` 内的三张图片。以下署名和许可仅适用于对应图片；网站模板的 MIT 许可证不替代这些图片的原有许可。

## 超弦理论：Calabi–Yau 五次流形的局部二维截面

- 文件：`assets/media/research/string-theory.jpg`。
- 作者：**Andrew J. Hanson, Indiana University**。
- 作品：*CalabiYau5.jpg*，六实维 Calabi–Yau 五次流形的局部二维截面可视化。它是数学可视化，不是额外维度的观测照片。
- [作者的大学主页](https://homes.luddy.indiana.edu/hansona/)。
- [原始来源和授权记录](https://commons.wikimedia.org/wiki/File:CalabiYau5.jpg)。
- [原始 JPEG](https://upload.wikimedia.org/wikipedia/commons/e/e3/CalabiYau5.jpg)，2048 × 2048。
- 采用的许可：[CC BY-SA 3.0](https://creativecommons.org/licenses/by-sa/3.0/)。来源页另列作者的署名授权；本站保留 CC BY-SA 3.0 标记。
- 处理：仓库保存原始 JPEG；网页使用 Hugo 等比缩放、转换生成的 WebP，保持完整构图和原色。对应图片及其派生版本继续遵守上述许可。

## 数学物理：A_Q 型线性 quiver

- 文件：`assets/media/research/mathematical-physics.svg`。
- 作者：**Jean-Emile Bourgine, Yutaka Matsuo, Hong Zhang**。
- 作品：*Holomorphic field realization of SHᶜ and quantum geometry of quiver gauge theories*, JHEP **04 (2016) 167**，**Figure 2: A_Q linear quiver**。
- [论文和许可说明](https://link.springer.com/article/10.1007/JHEP04(2016)167)。
- [出版社 PDF](https://link.springer.com/content/pdf/10.1007/JHEP04(2016)167.pdf)。
- 许可：[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)。
- 来源位置：PDF 第 13 页，论文页码 12。
- 处理：提取图 2 主体的矢量内容，移除周围正文、原图注和页边内容；图中节点、箭头、虚线、科学标记和颜色保持原样。文字转换为路径，以免浏览器缺少数学字体。
- 提取方法：PyMuPDF 1.26.6，`show_pdf_page` 的裁切区域为 `(130, 80, 465, 225)` PDF 点，原点在页面左上角；`get_svg_image(text_as_path=True)`。输出视窗为 335 × 145。
- 出版社 PDF 的 SHA-256：`5a4bce838dfd4d927502085db826f45e336f7dd8d9cb593bb48fe1e2d6a494aa`。
- SVG 的 SHA-256：`e6a2a75de7d3aa7c444d8ce146b175a0bb7c89a8b37b997b55ffbd19742a462c`。

## 引力波：双中子星并合前的引力波示意

- 文件：`assets/media/research/gravitational-waves.jpg`。
- 署名：**NASA's Goddard Space Flight Center/CI Lab**。
- 作品：*Doomed Neutron Stars Create Blast of Light and Gravitational Waves*，NASA SVS 12740 中的 `Neutron_Star_Merger_Still_1.jpg`。
- [原始来源和图注](https://svs.gsfc.nasa.gov/12740/)。
- [原始 JPEG](https://svs.gsfc.nasa.gov/vis/a010000/a012700/a012740/Neutron_Star_Merger_Still_1.jpg)，3840 × 2160。
- [NASA SVS 使用说明](https://svs.gsfc.nasa.gov/help/)：除单独注明者外，其内容属于公有领域。本图的明确署名为 NASA Goddard/CI Lab，不使用同页另有第三方署名的图片。
- 处理：仓库保存原始 JPEG；网页由 Hugo 等比缩小为 WebP，并在 16:9 图片框内显示。图为科学示意，不是引力波的直接光学照片。

## 维护约定

两个内容文件通过 `image`、`image_alt`、`image_fit`、`image_credit` 引用图片：

- `content/_index.md`
- `content/research/index.md`

`image` 的路径相对于 `assets/media/`。`image_fit: contain` 适合完整几何图和论文图；`cover` 适合构图允许轻微裁切的横向插图。`image_credit` 支持 Markdown 链接，页面以小号图注显示，图片本身可点击查看原图。

图片呈现的局部覆盖位于 `layouts/_partials/hbx/blocks/focus-areas/block.html`，基于项目固定版本的原生区块，仅扩展图片字段、完整显示、原图链接、替代文本和图注。升级 HugoBlox 时应核对这一处覆盖。
