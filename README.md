# APK 一键反编译工具（AI 增强版）

一个 Windows 下的 Android APK 反编译工具，**单个 EXE 文件、无需安装任何依赖**（内置 Java 运行环境），拖入 APK 即可完成反编译，并自动生成可供 AI 编程助手阅读的项目说明。

## 功能特性

- **拖拽反编译**：把 APK 拖到 EXE 图标上，或双击 EXE 选择文件（支持多选）
- **零依赖**：内置 Java 运行环境（JRE），目标电脑无需安装 Java
- **资源反编译**：基于 [Apktool](https://github.com/iBotPeaches/Apktool)，导出图片素材、布局文件、`AndroidManifest.xml` 等
- **源码导出**：基于 [JADX](https://github.com/skylot/jadx)，导出可直接阅读的 `.java` 源码文件
- **自动反混淆**：检测到代码混淆（类名为 a/b/c 等单字母）时，自动生成反混淆版源码 `deobf_sources\`，类名/方法名还原为可读别名（原名以注释保留），混淆应用也能顺畅阅读
- **中文源码查看器**：JADX-GUI 界面强制中文显示，并默认开启反混淆
- **AI 项目说明（AGENTS.md）**：自动生成项目说明书，包含应用信息、权限列表、启动入口、目录结构、源码包统计，把项目文件夹交给 AI 工具（DevEco Code / Cursor / Claude Code / Copilot 等）即可自动理解整个项目

## 使用方法

1. 下载 [Releases](../../releases) 中的 `APK-Decompiler.exe`（约 111MB，即「APK 一键反编译」工具）
2. 把任意 `.apk` 文件拖到 EXE 图标上
3. 等待完成（约 3~8 分钟），自动打开结果

```
xxx_project\                ← 反编译输出（与 APK 同目录）
├── sources\                ← Java 源码（JADX 导出，.java 文件可直接阅读）
├── deobf_sources\          ← 反混淆版源码（检测到混淆时自动生成，建议优先阅读）
├── resources\              ← 资源文件（图片素材 / 布局 / AndroidManifest.xml / smali）
└── AGENTS.md               ← AI 项目说明（自动生成）
```

首次运行会自动释放内置工具到 `%LOCALAPPDATA%\APKDecompile`（约 190MB）。

## 界面预览

```
╔══════════════════════════════════════════════════╗
║       APK 一键反编译工具（AI 增强版）v1.1        ║
║ 混淆还原 + 资源反编译 + 源码导出 + AI项目说明     ║
╚══════════════════════════════════════════════════╝

【1/5】正在导出 Java 源码（JADX 反编译引擎）...完成
【2/5】检测到代码混淆，正在反混淆（类名/方法名还原为可读别名）...完成
【3/5】正在反编译资源文件（图片 / 布局 / XML）...完成
【4/5】正在生成 AI 项目说明（AGENTS.md）...完成
【5/5】正在打开源码查看器（JADX-GUI 中文界面）...完成
```

## 环境要求

- Windows 10/11 64 位
- 无需安装 Java（内置 JRE 17）
- .NET Framework 4.x（Win10/11 系统自带）

## 从源码构建

本仓库只发布成品 EXE。内置的第三方组件：

- [Apktool](https://github.com/iBotPeaches/Apktool) — Apache License 2.0
- [JADX](https://github.com/skylot/jadx) — Apache License 2.0

感谢以上开源项目的贡献。

