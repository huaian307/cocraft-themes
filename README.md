# cocraft 主题工坊（Theme Workshop）

cocraft 面板的**社区主题仓库**。用户可以把自己设计的主题（配色 / 按钮图标 / 界面样式）投稿到这里，
其他人在面板「设置 → 主题工坊」里就能浏览、安装、套用。

## 主题格式

一个目录 = 一个主题：

```
themes/<id>/
  theme.json      # 清单（必需）
  preview.png     # 缩略图（可选，建议）
  theme.css       # 额外样式（可选）
  assets/         # 背景 / logo / 按钮图标（可选）
```

`theme.json`：

```json
{
  "id": "my-theme",
  "name": "我的主题",
  "author": "your-github-name",
  "version": "1.0.0",
  "description": "一句话描述",
  "mode": "dark",
  "preview": "preview.png",
  "vars": { "--paper": "#0d1117", "--hi": "#22d3ee" },
  "css": "theme.css",
  "icons": { "tools": "assets/wrench.svg" },
  "background": { "dark": "assets/night.jpg", "light": "assets/day.jpg" }
}
```

- `id`：`^[a-z0-9][a-z0-9-]{1,63}$`，不得用 `hiru` / `yoru` / `cocraft`。
- `mode`：`light` 或 `dark`。
- `vars` 覆盖面板的 CSS 变量（见 `schema/theme.schema.json`；常见的有
  `--paper --paper-2 --paper-3 --ink --ink-dim --ink-faint --hi --hi-deep --hi-wash --gold --gold-soft --sakura`）。
- `css` 可写任意样式（会注入面板）。**注意：主题不能包含/执行任何脚本；CSS 里的远程 `url()` 会被拦截，
  只允许引用主题自己的素材。**

## 投稿流程

1. Fork 本仓库。
2. 在 `themes/<你的 id>/` 放主题文件。
3. 把条目加进根目录 `catalog.json` 的 `themes` 数组。
4. 提 PR。合并后，面板下次刷新即可看到并安装。

## 许可

投稿即表示你同意以 MIT 或更宽松的许可分发你的主题；请确保素材你有权分发。
