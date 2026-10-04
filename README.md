<h1 align="center">
  <br>
  <img src="https://raw.githubusercontent.com/MXZhuoYao/BootAnimation/main/.github/assets/icon.png" alt="BootAnim" width="150">
  <br>
  BootAnim
  <br>
</h1>

<p align="center">
  <img alt="Platform" src="https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-blue">
  <img alt=".NET" src="https://img.shields.io/badge/.NET%20Framework-4.8-purple">
  <img alt="Dependencies" src="https://img.shields.io/badge/dependencies-none-success">
  <img alt="Version" src="https://img.shields.io/badge/version-v1.0.0-green">
  <img alt="License" src="https://img.shields.io/badge/license-free-lightgrey">
</p>

<p align="center">
  <img src="https://raw.githubusercontent.com/MXZhuoYao/BootAnimation/main/.github/assets/preview.jpg" alt="BootAnim 开机动画效果" width="880">
</p>

---

**BootAnim** 是一款 Windows 开机动画工具，让你在每次开机时全屏播放自己的一段 MP4，**播完自动进入登录界面** 🎬

它由一个以 LocalSystem 最高权限开机自启的服务，和一个被注入到登录桌面的全屏播放器组成。动画铺在登录界面**出现之前**，所以既不会看到登录界面抢先闪一下，也不会被其他启动项打断。

- 🎬 **任意 MP4** — 系统自带 Media Foundation 硬解，也可切换到外置 mpv 引擎
- 🖥️ **分辨率自适应** — 每次播放时实时枚举显示器，按物理像素贴合，显示模式变化会自动跟随
- 🎨 **无痕纯色填充** — 画面填不满的地方由窗口背景填充，颜色随便挑，没有黑边也没有接缝
- 🖼️ **多显示器** — 主显示器 / 全部显示器 / 指定某一块
- 🌗 **淡入淡出** — 让动画的出现和消失都柔和，不闪黑
- 🛡️ **不抢焦点** — 登录框始终能输密码，Ctrl+Alt+Del 始终有效
- ♻️ **崩溃自动重启** — 服务注册了 SCM 恢复策略，播放器崩溃会被看门狗拉起
- ⏱️ **绝不卡住登录** — 三重超时兜底，最坏情况也会在几十秒内让出屏幕
- 📦 **零外部依赖** — 只用 Windows 自带的 .NET Framework 4.8

## 📋 功能一览

### 播放

| 功能 | 说明 |
|------|------|
| 视频格式 | 任意 MP4（H.264 / HEVC 等，取决于系统解码器） |
| 填充方式 | contain 完整显示 / cover 铺满裁切 / stretch 拉伸铺满 |
| 留白颜色 | 任意纯色，十六进制或取色器 |
| 音量 | 0–100，可静音；默认静音（开机时音频设备常常还没就绪） |
| 淡入淡出 | 毫秒级可调 |
| 循环播放 | 可选 |
| 单次最长 | 秒，0 表示不限制 |
| 兜底强杀 | 秒，服务超过这个时间强制结束动画 |

### 运行方式

| 功能 | 说明 |
|------|------|
| 播放时机 | 登录前 / 登录后 / 自动（优先登录前，失败自动降级） |
| 每开机一次 | 只播一次，或每次登录都播 |
| 强制置顶 | 播放时持续抢回最顶层，不被其他启动项盖住 |
| 崩溃恢复 | SCM 恢复策略 1 / 2 / 5 秒三连重启 |
| 服务器兜底 | 服务不可用时自动降级为登录后播放，不会变成"什么都没有" |

## 📸 界面

### 安装向导

| 欢迎 | 选择安装位置 | 准备安装 | 安装进度 |
|:---:|:---:|:---:|:---:|
| <img src="https://raw.githubusercontent.com/MXZhuoYao/BootAnimation/main/.github/assets/install-1.png" width="200"> | <img src="https://raw.githubusercontent.com/MXZhuoYao/BootAnimation/main/.github/assets/install-2.png" width="200"> | <img src="https://raw.githubusercontent.com/MXZhuoYao/BootAnimation/main/.github/assets/install-3.png" width="200"> | <img src="https://raw.githubusercontent.com/MXZhuoYao/BootAnimation/main/.github/assets/install-4.png" width="200"> |

### 配置界面

<p align="center">
  <img src="https://raw.githubusercontent.com/MXZhuoYao/BootAnimation/main/.github/assets/config.png" alt="配置界面" width="620">
</p>

### 关于

<p align="center">
  <img src="https://raw.githubusercontent.com/MXZhuoYao/BootAnimation/main/.github/assets/about.png" alt="关于对话框" width="380">
</p>

---

## 安装

### 系统要求

- Windows **10 / 11**（x64）
- .NET Framework 4.8（Windows 自带，无需安装）

### 下载安装

从 [Releases](https://github.com/MXZhuoYao/BootAnimation/releases/latest) 下载 `BootAnim-v1.0.0-setup.exe`，双击运行。

安装向导共四步：欢迎 → 选择安装位置 → 确认 → 安装进度。安装位置默认是
`C:\Program Files\BootAnim`，可以点「浏览...」改到别的地方。

也可以下载 `BootAnim-v1.0.0-win64.zip` 绿色版，解压后双击 `安装.bat`。

> [!IMPORTANT]
> 安装包和可执行文件**没有数字签名**，首次运行可能出现 SmartScreen 提示，点「更多信息 → 仍要运行」即可。
>
> 安装会注册一个开机自启的服务 **BootAnim**（LocalSystem）。如果想撤销，在
> 「设置 → 应用 → 已安装的应用」里卸载即可。

---

## 使用

### 配置开机动画

1. 打开 **BootAnim 配置**（桌面快捷方式，或安装目录里的 `BootAnimCfg.exe`）
2. 选择你的 MP4
3. 挑一个留白填充色（画面填不满的地方会用它填满）
4. 点 **「保存并应用」**
5. 重启

> [!NOTE]
> 出厂配置里**视频是空的**，不选就什么都不播。点「全屏试播」会用内置演示片试播，
> 但**不会写进配置**。

### 试播

- **窗口试播** — 小窗口预览，不影响你做别的事
- **全屏试播** — 真实覆盖整屏，6 秒后自动结束
- **测试登录前可行** — 让服务真实注入一次安全桌面，屏幕上什么都不会出现，结果写在日志里

### 卸载

「设置 → 应用 → 已安装的应用 → **BootAnim 开机全屏动画**」，
或运行安装目录里的 `卸载.bat`。卸载会从注册表读回实际安装位置，装到别的盘也能清干净。

---

## 从源码构建

只需要 Windows 自带的 C# 编译器（`csc.exe`），**不需要 Visual Studio、不需要 .NET SDK、不需要联网**。

```bat
构建.bat        :: 编译三个 exe + 安装程序
发布.bat        :: 生成 zip + setup.exe + SHA256
测试规则.bat    :: 跑规则单元测试
```

或者：

```powershell
powershell -ExecutionPolicy Bypass -File .\build.ps1 -Target all
powershell -ExecutionPolicy Bypass -File .\make-release.ps1 -Version 1.0.0
```

### 项目结构

```
src/Common/    配置、日志、INI、Win32 互操作、显示器解析、服务安装器
src/Player/    全屏播放器（WPF，纯代码无 XAML）+ 极简封面窗口
src/Service/   服务、编排器、跨会话启动器、诊断
src/Config/    配置界面（WinForms，按 DPI 自适应缩放）
src/Setup/     向导式安装程序
src/Tests/     规则单元测试
```

> 想了解内部的实现细节和踩过的坑，见 **[技术笔记.md](技术笔记.md)**。

---

## 🛣️ Roadmap

- [x] 登录前全屏播放 + 播完自动进入登录界面
- [x] 分辨率自适应 + 纯色填充留白
- [x] 多显示器 / 淡入淡出 / 置顶守护
- [x] 向导式安装程序 + 自定义安装位置
- [x] 崩溃自动重启 + 三重超时兜底
- [x] 配置文件界面 + 一键恢复初始设置
- [ ] 支持多段视频按顺序播放
- [ ] 支持 GIF / 序列帧素材
- [ ] 配置界面加入实时预览缩略图
- [ ] 英文界面

---

## ❓ 常见问题

**开机没有动画？**
跑一下 `BootAnimSvc.exe --diag` 看服务状态和配置，再看
`%ProgramData%\BootAnim\logs\service-*.log` 里有没有 `pre-logon launch` 那一行，
失败原因会写在里面。

**登录界面闪了一下才出现动画？**
确认配置里 `PreLogonWaitForLogonUi=0`、`UseCoverWindow=1`，
然后用「测试登录前可行」确认你的系统允许向安全桌面注入。

**它会自己决定播什么吗？**
不会。出厂配置里视频是空的，不选就什么都不播。

更详细的排查见 **[使用手册.md](使用手册.md)**。

---

## 📄 许可证

Copyright (C) 2026 **ZhuoYao**. 保留所有权利。

按「原样」提供，不附带任何担保。详见 [LICENSE.txt](LICENSE.txt)。
随包的 `demo/sample.mp4` 仅用于功能演示，可自行删除或替换。

---

<p align="center">
  Made by ZhuoYao QQ:83015102
</p>
