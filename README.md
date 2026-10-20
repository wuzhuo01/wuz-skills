# wuz-skills

一个技术总监把 AI 当员工带时，攒下来的小工具 skill。每个 skill 是一个文件夹 + 一份 `SKILL.md`，Claude Code、Codex、Cursor 都能用。

A growing toolbox of small, practical Agent Skills. Works with Claude Code, Codex and Cursor.

## Skills

| Skill | 做什么 | 依赖 |
|---|---|---|
| [batch-image-compress](skills/batch-image-compress/) | 批量压缩 PNG/JPG，画质把关、保留透明、压大了退回原图，替代一次只能传十几张的在线压缩网站 | pngquant, oxipng, mozjpeg, dssim |

## 安装

**Claude Code**
```sh
git clone https://github.com/wuzhuo01/wuz-skills.git
cp -r wuz-skills/skills/batch-image-compress ~/.claude/skills/
```

**Cursor**：复制到项目里的 `.cursor/skills/`。
**Codex**：复制到 `~/.codex/skills/`。

## 怎么用：批量压缩图片

**1. 装压缩工具（一次就好）**
```sh
brew install pngquant oxipng mozjpeg dssim   # macOS
```

**2. 在 Claude Code / Cursor / Codex 里直接说**

> 帮我批量压一下 `./assets/ui` 里的图，用高质量档，输出到 `./assets/ui_min`

三个档位：
- **高质量**（默认）：几乎看不出区别，适合按钮、图标、带小字的 UI
- **均衡**：大约是 TinyPNG 的水平，体积通常能减 60% 左右
- **极限**：体积最小，适合背景大图

**3. 你会拿到**
- 新文件夹里的压缩图，**原图不会被改动**
- 一张表：每张图的原大小、新大小、压缩率、画质分，以及是否保留了原图
- 几张难压的图（渐变、半透明、小字）的前后放大对比

压完反而变大，或者画质不达标的图，会自动保留原图；透明背景会保留；已经压过的图再处理时会自动跳过。

## 目录结构

```
wuz-skills/
├── README.md
├── LICENSE              # MIT
├── NOTICE.md            # 第三方工具许可证说明
└── skills/
    └── <skill-name>/
        ├── SKILL.md     # 必须：何时用 + 步骤 + 验收
        ├── scripts/     # 可选
        └── templates/   # 可选
```

新增 skill：在 `skills/` 下建文件夹，写 `SKILL.md`，再在上面的表里加一行。

## 许可证

本仓库内容（skill 文字、脚本）使用 [MIT](LICENSE)。
skill 调用的外部工具**不随本仓库分发**，由使用者自行安装，各自遵守其许可证，见 [NOTICE.md](NOTICE.md)。
