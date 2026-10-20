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

装好后直接说「帮我批量压一下 ./assets 里的图」即可。

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
