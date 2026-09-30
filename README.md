# 🐦🚲 Pelican On A Bike · 鹈鹕骑车

一只戴着头盔、围着红围巾的鹈鹕骑着自行车前进。本仓库包含两个独立的网页小作品，分别用 **SVG 2D 动画** 和 **Three.js 3D 场景** 实现同一个主题。

两个项目都是**单个 HTML 文件**，无需构建、无需安装依赖，双击用浏览器打开即可运行。

| 文件 | 技术 | 风格 |
| --- | --- | --- |
| [`pelican-riding.html`](./pelican-riding.html) | 原生 SVG + CSS 动画 + JavaScript | 2D 海岸线横版小游戏 |
| [`pelican-threejs.html`](./pelican-threejs.html) | Three.js r128 + OrbitControls | 3D 乡间公路骑行场景 |

---

## 一、2D 版：`pelican-riding.html`

### 场景

白色鹈鹕骑着蓝色自行车沿海岸线前进，后座篮子里装着一条鱼。背景有远处的小岛和灯塔、有帆船的大海、沙滩、椰子树和遮阳伞，多层背景以不同速度向后移动，形成视差效果。

### 玩法与功能

- **跳起接鱼**：空中会飘来彩色的鱼，让鹈鹕跳起来用嘴接住。普通鱼 +1 分，金色的鱼（约 12% 概率出现）+3 分。
- **跳过石头**：路面会出现石头，需要及时起跳。
- **最高分记录**：最高分保存在浏览器 `localStorage` 中（键名 `pelican-best`），刷新页面不会丢失。
- **车铃与对话气泡**：点击车把上的车铃会响铃并弹出鹈鹕的台词，夜晚会说“晚上好~”。
- **昼夜切换**：白天与夜晚平滑过渡，夜晚天空出现闪烁的星星。
- **下雨**：开启后画面变暗，出现雨滴、地面水花和雨声。
- **速度调节**：滑块范围 0.4× ~ 2.2×，翅膀、围巾、速度线等动画节奏会随速度同步变化。
- **里程表**：实时显示已骑行的距离。
- **声音开关**：所有音效（车铃、跳跃、吃鱼、雨声）都由 Web Audio API 实时合成，没有外部音频文件，可一键静音。

### 操作方式

| 操作 | 按键 / 方式 |
| --- | --- |
| 跳起来 | `↑` / `W`，或点击画面，或点击「跳一下」按钮 |
| 按车铃 | `空格`，或点击车铃（车铃可用 Tab 聚焦后按回车） |
| 暂停 / 继续 | `P`，或点击「暂停」按钮 |
| 切换昼夜 | `N`，或点击「切到夜晚」按钮 |
| 开关下雨 | `R`，或点击「下雨」按钮 |
| 调整速度 | 拖动「速度」滑块 |

---

## 二、3D 版：`pelican-threejs.html`

### 场景

使用 Three.js 搭建的全屏 3D 场景：鹈鹕在乡间柏油公路上骑车，周围有草地、道路标线、云朵、太阳。场景带有实时阴影和雾效，鹈鹕会眨眼、转头，围巾随风飘动，车轮和脚踏按真实踏频转动。

### 功能

- **自由视角**：鼠标拖动旋转、滚轮缩放（触屏支持单指旋转、双指缩放）。
- **四个预设视角**：斜侧、侧面、正面、环绕（自动绕场景旋转），切换时镜头平滑过渡。
- **骑行控制**：加速、减速、向左 / 向右变道；按住生效，松开后车头自动回正，到路边无法继续外拐。
- **骑行仪表盘**：实时显示车速（km/h）、踏频（rpm）、齿比（34/18）和里程（km）。
- **速度滑块**：0 ~ 36 km/h。
- **车铃**：Web Audio 合成的双音铃声，车铃会同步晃动。
- **自动深色模式**：跟随系统的浅色 / 深色主题，深色时切换为夜晚天空、星星和较弱的光照。
- **自适应布局**：窄屏（手机竖屏）会自动调整相机视场角和控制栏布局，并适配刘海屏安全区域。

### 操作方式

| 操作 | 按键 / 方式 |
| --- | --- |
| 加速 / 减速 | `↑` `W` / `↓` `S`，或按住屏幕上的方向键 |
| 向左 / 向右变道 | `←` `A` / `→` `D`，或按住屏幕上的方向键 |
| 暂停 / 继续 | `空格`，或点击「暂停」按钮 |
| 按车铃 | `B`，或点击「按车铃」按钮 |
| 切换视角 | 数字键 `1` ~ `4`，或点击左上角视角按钮 |
| 旋转 / 缩放视角 | 鼠标拖动 / 滚轮，触屏拖动 / 双指缩放 |

### 外部依赖

3D 版通过 CDN 加载以下资源，因此**首次打开需要联网**：

- [Three.js r128](https://cdnjs.cloudflare.com/ajax/libs/three.js/r128/three.min.js)（cdnjs）
- [OrbitControls](https://cdn.jsdelivr.net/npm/three@0.128.0/examples/js/controls/OrbitControls.js)（jsDelivr）
- Google Fonts 的 [ZCOOL KuaiLe](https://fonts.google.com/specimen/ZCOOL+KuaiLe)（标题字体，加载失败时自动回退到系统字体）

2D 版完全不依赖任何外部资源，离线也能运行。

---

## 快速开始

### 方式一：直接打开

```bash
git clone https://github.com/jhlking/PelicanOnABike.git
cd PelicanOnABike
```

然后用浏览器（Chrome / Edge / Firefox / Safari）直接打开 `pelican-riding.html` 或 `pelican-threejs.html`。

### 方式二：本地静态服务器

如果浏览器对本地文件有限制，可以起一个静态服务器：

```bash
# Python 3
python -m http.server 8000

# 或 Node.js
npx serve .
```

然后访问 `http://localhost:8000/pelican-riding.html` 或 `http://localhost:8000/pelican-threejs.html`。

### 方式三：GitHub Pages 在线访问

在仓库 **Settings → Pages** 中，将 Source 设为 `main` 分支根目录，保存后即可通过以下地址访问：

- `https://jhlking.github.io/PelicanOnABike/pelican-riding.html`
- `https://jhlking.github.io/PelicanOnABike/pelican-threejs.html`

---

## 无障碍与体验细节

- **深色模式**：两个版本都支持 `prefers-color-scheme`，也可通过 `<html data-theme="light|dark">` 强制指定主题。
- **减少动态效果**：系统开启「减少动态效果」（`prefers-reduced-motion`）时，页面默认以暂停状态打开，3D 视角切换也不再使用过渡动画。
- **键盘可操作**：所有按钮都能用 Tab 聚焦并用回车 / 空格触发，焦点有清晰的描边提示；焦点在输入框上时快捷键不会误触。
- **屏幕阅读器**：SVG 场景带有 `<title>` 和 `<desc>` 描述，按钮使用 `aria-label` / `aria-pressed` 标注状态，比分变化通过 `aria-live` 播报。
- **容错**：`localStorage` 和 Web Audio 的调用都做了异常处理，在隐私模式或不支持音频的环境下页面依然正常运行。

## 目录结构

```
PelicanOnABike/
├── pelican-riding.html    # 2D SVG 版（海岸线接鱼小游戏）
├── pelican-threejs.html   # 3D Three.js 版（乡间公路骑行）
└── README.md
```

## 浏览器兼容性

推荐使用最新版的 Chrome、Edge、Firefox 或 Safari。3D 版需要浏览器支持 WebGL。
