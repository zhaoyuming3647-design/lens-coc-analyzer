<p align="center">
  <b>OptiCoC</b>: An Interactive 2D/3D Optical Defocus Blur Circle (CoC) Analyzer & Matrix Exporter
</p>

<p align="center">
  <a href="#中文说明">中文说明</a> •
  <a href="#english-documentation">English Documentation</a> •
  <a href="https://zhaoyuming3647-design.github.io/lens-coc-analyzer/">在线体验 / Live Demo</a>
</p>

---

<h2 id="中文说明">🇨🇳 中文说明</h2>

### 📌 项目简介
**OptiCoC** 是一个基于高斯薄透镜几何光学模型的纯前端单文件 Web 分析工具，专注于定量计算与对比两支摄影镜头在不同拍摄距离与背景距离下的**离焦弥散圆半径（Circle of Confusion Radius, $r$）**。

### ✨ 核心特性
- **支持中英双语（i18n）**：顶部一键切换中文/英文界面，图表坐标轴与导出文件表头实时同步。
- **2D / 3D 双模式视图**：
  - **2D 曲线（Retina 高清渲染）**：展示等构图（相同放大倍率 $M$）下虚化变化曲线，自动标出虚化反超临界点 $d^*$。
  - **3D 曲面（基于 Plotly.js）**：自由旋转对比两支镜头的弥散圆曲面，支持「同物距对比」与「等构图退后对比」。
- **设备自适应识别**：自动结合浏览器 UA 与视口宽度，自适应切换桌面双栏与移动端单列布局，并保留手动切换开关。
- **Excel 兼容 CSV 导出**：可导出单镜头的二维网格矩阵及双镜头汇总明细表（内置 UTF-8 BOM，Excel 打开不乱码）。

### 📐 核心光学公式
设镜头焦距为 $f$，光圈值为 $F$，对焦物距为 $u_0$，背景距主体距离为 $d$，焦平面弥散圆半径 $r$ 为：

$$r = \frac{c}{2} = \frac{f^2}{2 \cdot F} \cdot \frac{\vert{}d\vert{}}{(u_0 + d)(u_0 - f)}$$

在**等构图（放大倍率 $M = \frac{f}{u_0 - f}$ 恒定）**基准下，两支镜头虚化光斑大小完全相等的**临界背景距离 $d^*$**：

$$d^* = \left(1 + \frac{1}{M}\right) \cdot \frac{f_1 f_2 (F_2 - F_1)}{f_2 F_1 - f_1 F_2}$$

### 🤝 致谢
本项目在光学算法推导、数学建模与前端工程实现过程中，得到了 **Google Gemini** 的全流程结对编程协助：
1. **光学公式推导**：协助推导高斯薄透镜离焦弥散圆精确计算公式，并推导出等构图条件下虚化反超临界距离 $d^*$ 的解析表达式；
2. **可视化实现**：协助编写了基于原生 HTML5 Canvas 的高分屏 Retina 抗锯齿 2D 绘图逻辑，以及基于 Plotly.js 的 3D 双曲面交互对比图表；
3. **架构与工程**：协助设计了零构建单文件响应式架构，实现了设备模式自适应检测、中英双语国际化（i18n）字典驱动以及支持 Excel 直接读取的 CSV 导出模块。

---

<h2 id="english-documentation">🇬🇧 English Documentation</h2>

### 📌 Overview
**OptiCoC** is a zero-dependency, single-file interactive web application based on Gaussian thin-lens optical models. It calculates, visualizes, and exports the **Circle of Confusion (CoC) radius ($r$)** across focus distances ($u_0$) and background offsets ($d$).

### ✨ Key Features
- **Bilingual Interface (i18n)**: Seamless one-click switching between English and Chinese across all UI elements, charts, and CSV headers.
- **2D / 3D Dual Visualization**:
  - **2D Curve (Retina Crisp Rendering)**: Evaluates bokeh growth curves under identical framing, pinpointing the crossover distance $d^*$.
  - **3D Surface (Powered by Plotly.js)**: Renders interactive 3D blur response surfaces for both same-distance and equivalent framing modes.
- **Smart Responsive Layout**: Automatically adapts to mobile vs. desktop viewports via User-Agent and media queries, with manual override support.
- **Excel-Compatible CSV Export**: Generates 2D matrix grids and detailed comparison datasets with UTF-8 BOM encoding for seamless Excel import.

### 📐 Optical Formulation
For a lens with focal length $f$, f-number $F$, subject focus distance $u_0$, and background distance relative to the subject $d$, the defocus blur circle radius $r$ on the sensor plane is:

$$r = \frac{c}{2} = \frac{f^2}{2 \cdot F} \cdot \frac{\vert{}d\vert{}}{(u_0 + d)(u_0 - f)}$$

Under **identical framing (constant magnification $M = \frac{f}{u_0 - f}$)**, the crossover background distance $d^*$ where two lenses produce identical blur spot size is:

$$d^* = \left(1 + \frac{1}{M}\right) \cdot \frac{f_1 f_2 (F_2 - F_1)}{f_2 F_1 - f_1 F_2}$$

### 🤝 Acknowledgments
This project was developed with the assistance of **Google Gemini** as an AI pair programmer throughout the theoretical modeling and frontend implementation:
1. **Optical Formulation**: Assisted in deriving the exact thin-lens defocus blur circle formula and constructing the analytical solution for the crossover background distance $d^*$ under equivalent framing;
2. **Visualization Engineering**: Assisted in implementing the high-DPI Retina antialiased 2D canvas plotting engine and the Plotly.js 3D dual-surface interactive comparison diagram;
3. **Architecture & Tooling**: Assisted in designing the zero-build single-file responsive architecture, environment-based device detection, bilingual i18n localization engine, and UTF-8 BOM Excel-compatible CSV export modules.

---

## 🚀 在线使用 / Quick Start

- **在线直接访问 / Live Demo**：[https://zhaoyuming3647-design.github.io/lens-coc-analyzer/](https://zhaoyuming3647-design.github.io/lens-coc-analyzer/)
- **本地运行 / Local Run**：克隆仓库后，直接用任意浏览器双击打开 `index.html` 即可：

```bash
git clone [https://github.com/zhaoyuming3647-design/lens-coc-analyzer.git](https://github.com/zhaoyuming3647-design/lens-coc-analyzer.git)
cd lens-coc-analyzer
open index.html
