# Hello Together Minecraft Launcher

> 一个纯网页的单文件 Minecraft 启动器 UI —— 100% Vibe Coding。

**HTML**（Hello Together Minecraft Launcher）是一个**只有界面、没有真实 JVM 启动逻辑**的 Minecraft 启动器概念演示。它用一份 HTML 文件把启动器该有的样子做出来：版本列表、资源检索、账户皮肤预览、联机房间界面、主题定制、板块编排——但点“启动”并不会真的拉起游戏进程。

它不是“又一个启动器”，而是一块**可交互的 UI 试验田**：适合拿来整活、截图，或者作为你自己启动器 UI 的起点。

> **NOT AN OFFICIAL MINECRAFT PRODUCT. NOT APPROVED BY OR ASSOCIATED WITH MOJANG OR MICROSOFT.**  
> “Minecraft” is a registered trademark of Mojang Synergies AB. This project is an unofficial, fan-made UI experiment and is not affiliated with, sponsored by, or endorsed by Mojang or Microsoft.

---

## 简介

HTML 启动器只有一个主 HTML 文件。打开即用，不需要构建、不需要安装、不需要 Node.js。所有的“数据”都活在浏览器的 `localStorage` 里：你登记的版本、下载过的资源、调过的主题色、摆过的板块顺序，关掉页面再回来还在——但换一台设备就没了，所以它本质上是一个**本地优先的 UI 沙盒**，而不是真正的版本管理器。

版本清单、Modrinth 检索、CurseForge 检索（需自备 API Key）、Mojang 皮肤提取这些网络请求是真实的；client.jar 和资源文件也会通过浏览器下载到本地。但“启动进度”是演示，不会产生 Java 进程。

### 它是 / 不是

- ✅ 一个**单文件 HTML** 的 Minecraft 启动器界面实现
- ✅ 一套**可参考、可改造**的 UI 设计（CC BY-SA 4.0）
- ❌ 不包含 JVM 启动逻辑
- ❌ 不扫描你磁盘上的 `.minecraft` 目录
- ❌ 不是 Mojang / Microsoft 的官方产品

---

## 功能

### 界面与定制

- **主题色**：8 套预设 + 自定义 hex / 取色器
- **明暗模式**：浅色 / 深色
- **背景**：纯色、网格、色晕、暖光，或上传自定义图片（自动压缩，存在 localStorage）
- **圆角、密度、动效**：滑杆 / 开关实时生效
- **板块系统**：引导页与启动页的板块可以**隐藏、排序、在两端之间移动**

### 账户与皮肤

- **正版 ID 提取皮肤**：填 ID → 从公开皮肤接口取回展开图 → 视为登录成功（不验证密码）
- **离线账户**：自传 64×32 / 64×64 皮肤展开图
- **3D 皮肤预览**：Canvas 2D 正交投影 + 贴图仿射，支持拖拽旋转、滚轮缩放、**站立 / 跑步 / 坐下**三种姿势，以及双层皮肤渲染

### 版本与资源

- 版本清单真实读取 Mojang `version_manifest_v2`，可切 **BMCLAPI 镜像**（跨域失败时自动回退官方）
- 支持**同时下载 client.jar**（流式下载，带进度条）
- **Modrinth** 匿名检索模组、整合包、数据包、资源包、光影
- **CurseForge** 检索需在设置中填入免费 API Key
- 资源详情支持**大版本 → 加载器+精确版本 → 文件版本**三层选择，前置模组一并列出并下载
- 下载后**自动登记到所选版本**，可在“我的资源”或版本设置中停用 / 移除

### 联机（演示）

- 房主生成邀请码，房客凭码加入
- 房间成员列表、延迟占位、人数上限
- **不建立真实隧道**，仅演示流程

### 其他

- 键盘快捷键（Ctrl/⌘ + 1…5 切导航，Ctrl/⌘ + K 聚焦搜索，Ctrl/⌘ + D 切明暗）
- 配置导出 / 导入 JSON
- 活动日志、下载记录
- 响应式布局（桌面三栏 → 移动端底部导航）

---

## 快速开始

1. 下载或 clone 本仓库。
2. 用浏览器打开 `HTML.html`（或你命名的主 HTML 文件）。
3. 想装版本：去 **下载 → 原版游戏** 挑一个，下载后会自动登记。
4. 想登录：点启动页的 **登录 / 切换**，正版填 ID 取皮肤，离线自传皮肤图。

不需要 npm，不需要构建工具，不需要服务器。

---

## 已知限制

| 限制 | 说明 |
|---|---|
| 不启动游戏 | 没有 JVM，没有 Java 进程，启动进度是演示 |
| 不扫描本地版本 | 浏览器无法读取磁盘上的 `.minecraft`，版本靠“下载登记”或“手动登记” |
| 数据随浏览器走 | 清缓存 / 换浏览器会丢失，建议用导出配置备份 |
| 部分接口受跨域影响 | BMCLAPI 镜像可能不放行 CORS，会自动回退官方源 |
| 联机是界面演示 | 不建立真实 P2P 隧道，适合展示流程，不适合真的联机 |

---

## 贡献

这是一个整活项目，不是像 HMCL 或 PCL 那样的严肃工程。如果你发现了 bug、想加功能、或者只是觉得某个交互可以更顺手：

- 在 GitHub 上**开 Issue** 聊聊
- 或者 **Fork + Pull Request**

因为是 100% Vibe Coding，代码风格没有严格规范，但请尽量保持单文件、不引入构建步骤。

---

## 作者

**一只宇杰吖**

- GitHub：[@YuJieYawa](https://github.com/YuJieYawa)
- 仓库：https://github.com/YuJieYawa/HTML-WebMCL
