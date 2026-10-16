<p align="center">
  <b>OptiCoC</b>: An Interactive 2D/3D Optical Defocus Blur Circle (CoC) Advanced Analyzer & Matrix Exporter
</p>

<p align="center">
  <a href="#中文说明">中文说明</a> •
  <a href="#english-documentation">English Documentation</a> •
  <a href="https://zhaoyuming3647-design.github.io/lens-coc-analyzer/">在线体验 / Live Demo</a>
</p>

---

<h2 id="中文说明">🇨🇳 中文说明</h2>

### 📌 项目简介
**OptiCoC** 是一个基于高斯薄透镜几何光学模型的纯前端单文件 Web 光学分析工具，专注于定量计算与对比两支摄影镜头在不同拍摄距离与背景距离下的**离焦弥散圆半径（Circle of Confusion Radius, $r$）**。

### ✨ 核心特性（v1.2 升级版）
- **画幅转换计算器与多传感器独立配置**：
  - 镜头 1 与镜头 2 支持独立设置感光元件尺寸，内置全画幅 35mm、中画幅（4433 / 5440 / 645 / 6x6）、APS-C、M4/3、大画幅（4x5 / 8x10）及 Super 35 / ARRI LF 等数字、胶片与广播电影预设，并支持自定义传感器宽高。
  - 实时解算各画幅下的横向视场角（HFOV），支持跨画幅等构图换算。
- **双构图驱动模式（主体占比 vs. 相平面工作物距）**：
  - **主体画面占比（$M$）**：基于像方放大率锁定构图比例。
  - **相平面物距调节（$L$）**：允许指定单支镜头的机身芯片标记（Φ）到主体物理总距离 $L = u_0 + v_0$，程序自动反求高斯主平面物距 $u_0$ 并精确推导另一支镜头的等构图物距。
- **全局英公制单位自由切换（Metric / Imperial）**：
  - 支持米（$\text{m}$）与英尺（$\text{ft}$）全局一键切换，输入框、2D/3D 坐标轴刻度及矩阵报表自动进行双向无缝换算。
- **支持中英双语（i18n）**：顶部一键切换中文/英文界面，所有光学说明与导出表头完全同步。
- **2D / 3D 双模式视图**：
  - **2D 曲线（Retina 高清渲染）**：展示等构图下虚化变化曲线，自动标出虚化反超临界点 $d^*$。
  - **3D 曲面（基于 Plotly.js）**：自由旋转对比两支镜头的弥散圆曲面，支持「同物距对比」与「等构图退后对比」。
- **Excel 兼容 CSV 导出**：可导出单镜头的二维网格矩阵及双镜头汇总明细表（内置 UTF-8 BOM，Excel 打开不乱码）。

### 📐 核心光学公式
设镜头焦距为 $f$，光圈值为 $F$，对焦物距为 $u_0$，背景距主体距离为 $d$，焦平面弥散圆半径 $r$ 为：

$$r = \frac{c}{2} = \frac{f^2}{2 \cdot F} \cdot \frac{\vert{}d\vert{}}{(u_0 + d)(u_0 - f)}$$

焦平面总距（Sensor-to-Subject Distance）$L$ 与主平面物距 $u_0$ 满足二次方程：

$$L = u_0 + v_0 = u_0 + \frac{f \cdot u_0}{u_0 - f} \implies u_0^2 - L \cdot u_0 + L \cdot f = 0$$

在**等构图（相对横向画幅占比恒定）**基准下，两支镜头虚化光斑大小相等的**临界背景距离 $d^*$**：

$$d^* = \frac{D_2 M_2 u_{0,1} - D_1 M_1 u_{0,2}}{D_1 M_1 - D_2 M_2}$$

### 🤝 致谢
本项目在光学算法推导、数学建模与前端工程实现过程中，得到了 **Google Gemini** 的全流程结对编程协助：
1. **光学公式推导**：协助推导高斯薄透镜焦平面物距二次反解方程、跨画幅等效放大率比例换算，以及虚化反超临界距离 $d^*$ 的解析表达式；
2. **可视化实现**：协助编写了基于原生 HTML5 Canvas 的高分屏 Retina 抗锯齿 2D 绘图逻辑，以及基于 Plotly.js 的 3D 双曲面交互对比图表；
3. **架构与工程**：协助设计了零构建单文件响应式架构，实现了设备模式自适应检测、传感器画幅预设数据库、英公制单位换算管道、双语国际化（i18n）驱动与 Excel 兼容的 CSV 矩阵导出模块。

---

<h2 id="english-documentation">🇬🇧 English Documentation</h2>

### 📌 Overview
**OptiCoC** is a zero-dependency, single-file interactive web application based on Gaussian thin-lens optical models. It calculates, visualizes, and exports the **Circle of Confusion (CoC) radius ($r$)** across focus distances ($u_0$) and background offsets ($d$).

### ✨ Key Features (v1.2 Update)
- **Sensor Format Converter & Independent Dual-Sensor Setup**:
  - Independent sensor dimension setup for Lens 1 and Lens 2, featuring built-in presets for 35mm Full Frame, Medium Format (4433 / 5440 / 645 / 6x6), APS-C, M4/3, Large Format (4x5 / 8x10), Super 35, ARRI LF, as well as customizable sensor width/height.
  - Dynamically calculates Horizontal Field of View (HFOV) and handles cross-format equivalent framing.
- **Dual Framing Reference Modes (Magnification vs. Sensor Distance)**:
  - **Framing Ratio ($M$)**: Locks composition based on physical magnification relative to sensor width.
  - **Sensor-to-Subject Distance ($L$)**: Adjusts the camera focal plane mark (Φ) to subject physical distance ($L = u_0 + v_0$). Solves the optical object distance $u_0$ quadratically and derives the equivalent distance for the counterpart lens.
- **Metric / Imperial Global Unit Switching**:
  - One-click toggling between meters ($\text{m}$) and feet ($\text{ft}$) with seamless coordinate scale recalculations across inputs, 2D/3D charts, and data matrices.
- **Bilingual Interface (i18n)**: Seamless one-click switching between English and Chinese across all UI elements, charts, and CSV headers.
- **2D / 3D Dual Visualization**:
  - **2D Curve (Retina Crisp Rendering)**: Evaluates bokeh growth curves under identical framing, pinpointing the crossover distance $d^*$.
  - **3D Surface (Powered by Plotly.js)**: Renders interactive 3D blur response surfaces for both same-distance and equivalent framing modes.
- **Excel-Compatible CSV Export**: Generates 2D matrix grids and detailed comparison datasets with UTF-8 BOM encoding for seamless Excel import.

### 📐 Optical Formulation
For a lens with focal length $f$, f-number $F$, subject focus distance $u_0$, and background distance relative to the subject $d$, the defocus blur circle radius $r$ on the sensor plane is:

$$r = \frac{c}{2} = \frac{f^2}{2 \cdot F} \cdot \frac{\vert{}d\vert{}}{(u_0 + d)(u_0 - f)}$$

The total focal-plane distance $L$ and the optical object distance $u_0$ satisfy:

$$L = u_0 + v_0 = u_0 + \frac{f \cdot u_0}{u_0 - f} \implies u_0^2 - L \cdot u_0 + L \cdot f = 0$$

Under **equivalent framing (constant relative sensor coverage)**, the crossover background distance $d^*$ where two lenses produce identical blur spot size is:

$$d^* = \frac{D_2 M_2 u_{0,1} - D_1 M_1 u_{0,2}}{D_1 M_1 - D_2 M_2}$$

### 🤝 Acknowledgments
This project was developed with the assistance of **Google Gemini** as an AI pair programmer throughout the theoretical modeling and frontend implementation:
1. **Optical Formulation**: Assisted in solving thin-lens quadratic focal plane distances, cross-format magnification scaling, and the crossover distance $d^*$ under equivalent framing;
2. **Visualization Engineering**: Assisted in implementing the high-DPI Retina antialiased 2D canvas plotting engine and the Plotly.js 3D dual-surface interactive comparison diagram;
3. **Architecture & Tooling**: Assisted in designing the zero-build single-file responsive architecture, multi-format sensor database, metric/imperial unit pipeline, bilingual i18n localization engine, and UTF-8 BOM Excel-compatible CSV export modules.

---

## 🚀 在线使用 / Quick Start

- **在线直接访问 / Live Demo**：[https://zhaoyuming3647-design.github.io/lens-coc-analyzer/](https://zhaoyuming3647-design.github.io/lens-coc-analyzer/)
- **本地运行 / Local Run**：克隆仓库后，直接用任意浏览器双击打开 `index.html` 即可：

```bash
git clone [https://github.com/zhaoyuming3647-design/lens-coc-analyzer.git](https://github.com/zhaoyuming3647-design/lens-coc-analyzer.git)
cd lens-coc-analyzer
open index.html
