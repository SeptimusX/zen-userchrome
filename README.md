# Zen Browser userChrome

针对 **Zen 1.24.x**（Firefox 159）的 `userChrome.css` 小调整，主要解决侧边栏文字偏大、右键菜单在 Windows 11 Mica 下没有边框、以及 Tab 和菜单行偏高的问题。

## 包含的改动

- 侧边栏标签标题、「新建标签页」行字号缩小到原来的 90%
- 右键菜单 / 弹出面板恢复 1px 可见边框（Mica 下 Zen 把边框交给 DWM，DWM 不绘制时菜单没有轮廓）
- Tab 行高从约 45px 收紧到约 39px
- 右键菜单每行高度收紧（上下内边距 `0.5em` → `0.3em`）

## 安装

1. 把 `userChrome.css` 放到当前配置文件的 `chrome` 目录：
   - Windows：`%APPDATA%\zen\Profiles\<profile>\chrome\userChrome.css`
2. 在 `about:config` 中把 `toolkit.legacyUserProfileCustomizations.stylesheets` 设为 `true`。
3. 完全退出 Zen 再重新打开。

## 微调

- Tab 高度：修改 `#tabbrowser-tabs` 里的 `--tab-min-height`（默认 30px），不要低于 26px。
- 菜单行高：修改 `menupopup` 里的 `--menuitem-padding-block`（默认 0.3em；更紧凑可用 0.2em）。
- 菜单边框透明度：修改 `--panel-border-color` 中的 0.22。

## 说明

本仓库不包含 `user.js`。与个人环境相关的偏好（例如紧凑模式 `zen.view.compact.enable-at-startup`）请自行在 `about:config` 中设置。
