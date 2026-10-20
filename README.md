# wuz-skills

一个技术总监把 AI 当员工带时，攒下来的小工具 skill。每个 skill 是一个文件夹 + 一份 `SKILL.md`，Claude Code、Codex、Cursor 都能用。

A growing toolbox of small, practical Agent Skills. Works with Claude Code, Codex and Cursor.

## Skills

| Skill | 做什么 | 依赖 |
|---|---|---|
| [batch-image-compress](skills/batch-image-compress/) | 批量压缩 PNG/JPG，画质把关、保留透明、压大了退回原图，替代一次只能传十几张的在线压缩网站 | pngquant, oxipng, mozjpeg, dssim |

## 安装

**Claude Code（推荐，以后更新方便）**
```sh
claude plugin marketplace add wuzhuo01/wuz-skills
claude plugin install wuz-skills@wuz-skills
```
更新：`claude plugin marketplace update wuz-skills && claude plugin update wuz-skills@wuz-skills`

**Cursor**：把 `skills/` 下要用的文件夹复制到项目里的 `.cursor/skills/`。
**Codex**：复制到 `~/.codex/skills/`。

**或者直接让 AI 装**：对你的 AI 编程工具说「帮我安装 https://github.com/wuzhuo01/wuz-skills」，它会按下面这段说明操作。

### 给 AI 的安装说明

如果你是正在帮用户安装本仓库的 AI agent，请按顺序执行：

1. **先判断你是哪个工具**，只装到对应位置：
   - Claude Code：运行上面两条 `claude plugin` 命令即可，不要手动复制。
   - Cursor：复制到当前项目的 `.cursor/skills/<skill-name>/`；用户说要全局用时复制到 `~/.cursor/skills/`。
   - Codex：复制到 `~/.codex/skills/<skill-name>/`。
   - 其他工具：问用户它的 skills 目录在哪，不要猜。
2. **问用户要装哪些 skill**，默认全装；只复制 `skills/` 下的文件夹，不复制 README、LICENSE 等仓库文件。
3. **装依赖**：读每个 skill 的 `SKILL.md`，按「准备工具」一节装依赖（例如 macOS 上 `brew install pngquant oxipng mozjpeg dssim`）。装之前告诉用户要装什么；装不上就如实说明，不要换别的工具代替。
4. **验证**：确认目标目录下有 `<skill-name>/SKILL.md`，依赖命令都能运行（例如 `pngquant --version`），然后告诉用户装了哪些 skill、各放在哪、怎么用一句话调用。
5. 不要修改用户项目里的其他文件。

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
├── .claude-plugin/      # Claude Code 插件市场配置（其他工具会忽略）
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
