<p align="center">
  <b>OptiCoC</b>: An Interactive 2D/3D Optical Defocus Blur Circle (CoC) Analyzer & Matrix Exporter
</p>

<p align="center">
  <a href="#中文说明">中文说明</a> •
  <a href="#english-documentation">English Documentation</a> •
  <a href="#快速使用--quick-start">在线演示 / Quick Start</a>
</p>

---

<h2 id="中文说明">🇨🇳 中文说明</h2>

### 📌 项目简介
**OptiCoC** 是一个基于高斯薄透镜几何光学模型的纯前端单文件 Web 工具，专注于定量分析和可视化摄影镜头在**不同拍摄距离（$u_0$）**与**不同背景距离（$d$）**下的**离焦弥散圆半径（Circle of Confusion Radius, $r$）**。

### ✨ 核心特性
- **2D / 3D 双模态交互**：
  - **2D 曲线**：支持等构图（相同主体放大倍率 $M$）下虚化变化曲线对比，自动计算并标出虚化反超临界点 $d^*$。
  - **3D 曲面**：基于 Plotly.js，支持自由旋转，提供「同物距对比」与「等构图对比（含三维反超交线）」两种视角。
- **设备自适应识别**：结合浏览器 User-Agent 与视口宽度，自动在桌面端双栏与移动端单列布局间无缝切换，支持手动覆盖。
- **Excel 兼容 CSV 导出**：可导出单镜头的二维网格矩阵 CSV 及双镜头汇总明细表（内置 UTF-8 BOM，Excel 直接双击打开不乱码）。

### 📐 核心光学公式
设镜头焦距为 $f$，光圈值为 $F$，对焦物距为 $u_0$，背景距主体距离为 $d$，焦平面弥散圆半径 $r$ 为：

$$r = \frac{c}{2} = \frac{f^2}{2 \cdot F} \cdot \frac{\vert{}d\vert{}}{(u_0 + d)(u_0 - f)}$$

在**等构图（放大倍率 $M = \frac{f}{u_0 - f}$ 恒定）**基准下，两支镜头（$f_1, F_1$ 与 $f_2, F_2$）虚化光斑大小完全相等的**临界背景距离 $d^*$**：

$$d^* = \left(1 + \frac{1}{M}\right) \cdot \frac{f_1 f_2 (F_2 - F_1)}{f_2 F_1 - f_1 F_2}$$

---

<h2 id="english-documentation">🇬🇧 English Documentation</h2>

### 📌 Overview
**OptiCoC** is a zero-dependency, single-file interactive web application based on Gaussian thin-lens optical models. It provides rigorous mathematical calculation, 2D/3D visualization, and dataset export for the **Circle of Confusion (CoC) radius ($r$)** across varying focus distances ($u_0$) and background offsets ($d$).

### ✨ Key Features
- **2D / 3D Dual Visualization**:
  - **2D Curve**: Compares background blur progression under identical framing (constant magnification $M$), dynamically highlighting the crossover distance $d^*$.
  - **3D Surface**: Powered by Plotly.js, rendering interactive 3D blur response surfaces with toggles for "Same Focus Distance" and "Equivalent Framing" modes.
- **Smart Responsive Layout**: Automatically detects mobile vs. desktop environments via User-Agent and viewport media queries, with manual override support.
- **Excel-Compatible CSV Export**: One-click generation of 2D matrix grids and detailed comparison datasets with UTF-8 BOM encoding for seamless Excel import.

### 📐 Optical Formulation
For a lens with focal length $f$, f-number $F$, subject focus distance $u_0$, and background distance relative to the subject $d$, the defocus blur circle radius $r$ on the sensor plane is:

$$r = \frac{c}{2} = \frac{f^2}{2 \cdot F} \cdot \frac{\vert{}d\vert{}}{(u_0 + d)(u_0 - f)}$$

Under **identical framing (constant magnification $M = \frac{f}{u_0 - f}$)**, the crossover background distance $d^*$ where two lenses produce identical bokeh spot diameters is:

$$d^* = \left(1 + \frac{1}{M}\right) \cdot \frac{f_1 f_2 (F_2 - F_1)}{f_2 F_1 - f_1 F_2}$$

---

<h2 id="快速使用--quick-start">🚀 快速使用 / Quick Start</h2>

本项目为**零构建（Zero-Build）单文件应用**：
1. 克隆或下载本仓库中的 `index.html`。
2. 双击直接在任意现代浏览器中运行；或通过 **GitHub Pages** 直接在线访问。

```bash
# Clone the repository
git clone [https://github.com/your-username/OptiCoC.git](https://github.com/your-username/OptiCoC.git)

# Open index.html in your browser
open OptiCoC/index.html
