# SougouEmojiFixer

<div align="center">
  <img src="https://raw.githubusercontent.com/250king/SougouEmojiFixer/master/screenshots/logo.png" width="96" height="96" alt="SougouEmojiFixer Logo"/>
</div>

为搜狗输入法小米版补全并统一 Unicode Emoji 的 LSPosed 模块。

> **源码仓库：** https://github.com/250king/SougouEmojiFixer

搜狗自带表情包的 Unicode 覆盖不全、风格不统一（符号、旗帜等用系统字体），本模块用完整且风格统一的 **Noto Emoji** 替换搜狗的表情分组，并支持对表情分组进行排序管理。

## 功能特性

- **补全 Unicode Emoji**：从 Unicode 官方 `emoji-test.txt` 拉取数据，支持 Emoji 11.0 ~ 17.0（默认最新稳定版）。
- **统一风格**：所有表情（含旗帜、符号、肤色变体、ZWJ 组合、双肤色组合）统一使用 Noto Emoji 风格。
- **按系统支持过滤**：自动检测当前系统字库缺失的表情并跳过；也可选择“保留系统缺字”（强行全部安装）。
- **肤色合并**：把 5 种肤色变体合并成一条入口，通过搜狗自带的选择器切换；完整双肤色矩阵自动生成对应父条目。
- **可选资格形式**：可包含 `minimally-qualified` / `unqualified` 序列。
- **图片源可选**：GitHub 源站或 jsDelivr 镜像。
- **分组排序管理**：拖拽 / 箭头调整分组顺序，并写入搜狗包目录的排序值；搜狗自生成的“组合”包（ID 2）也纳入排序管理（仅排序，不补齐）。
- **自动重载**：安装 / 排序完成后自动结束搜狗进程，下次启动即生效，无需重启手机。

## 环境要求

- Android 8.0（API 26）及以上，已 root
- 已安装 LSPosed
- 搜狗输入法小米版（`com.sohu.inputmethod.sogou.xiaomi`）
- 搜狗输入法已至少打开过一次 Emoji 面板，用于生成 `emojipackage` 目录

## 安装与使用

1. 安装本模块 APK。
2. 在 LSPosed 中启用模块，并将作用域勾选为 **搜狗输入法小米版**。
3. 重启或结束搜狗进程使模块生效。
4. 打开模块 App，选择 Unicode 版本后点击「安装 / 重新安装 Emoji」。
5. 安装完成后搜狗会自动重载，新表情即可使用。
6. 可在「排序」页面调整表情分组顺序并保存。

## 工作原理

搜狗的表情分组存储在数据目录的 `sogou/emojipackage/` 下，目录名为 `{分组ID}_{排序值}`。本模块解析 Unicode 官方 Emoji 数据，从 Noto Emoji 获取对应图片，并重建搜狗的 Emoji 分组数据与 `info.xml` / `version.json`，从而补齐缺失表情并统一显示风格。

模块主要处理搜狗内置表情分组 ID 3–23；搜狗自动生成的“组合”包（ID 2）只参与排序，不做下载或补齐。

## 已知问题

部分输入环境（如 QQ、部分 Web 输入框）可能无法按预期组合部分 Emoji，出现肤色变体或 ZWJ 序列拆分显示的情况，目前仍在研究优化。

相关截图：

![QQ 中的拆分显示](https://raw.githubusercontent.com/250king/SougouEmojiFixer/master/screenshots/qq-break-apart.jpg)

![浏览器中的拆分显示](https://raw.githubusercontent.com/250king/SougouEmojiFixer/master/screenshots/browser-break-apart.jpg)

## 未来计划

当前主要支持搜狗输入法小米版。由于不同定制版和官方版在 Emoji 数据结构上较为接近，后续计划逐步适配其他系统定制版及官方版（`com.sohu.inputmethod.sogou`）。

## 源码与问题反馈

- Source: https://github.com/250king/SougouEmojiFixer
- Issues: https://github.com/250king/SougouEmojiFixer/issues

## 许可证

GPL-3.0 © 2026 250king

## 免责声明

本项目仅供学习与技术研究使用。请勿将其用于任何违反软件许可协议或当地法律法规的用途。使用本模块造成的任何后果由使用者自行承担。
