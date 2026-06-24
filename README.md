# WeChat Daily Report Skill

<!-- SIUSER-REPO-GUIDE:START -->
## 项目介绍 / Project Introduction

### 中文
微信群日报 Skill：把微信群聊整理成社区运营日报和 AI 摘要报告。

### English
WeChat group daily-report skill for turning chats into community operation reports and AI summaries.

## 使用方式 / Usage

### 中文
1. 先阅读 `SKILL.md`，确认触发场景、输入要求和执行步骤。
2. 按仓库 README 的安装方式复制或安装 Skill。
3. 在真实任务中调用前，先用示例或测试脚本做一次小范围验证。

### English
1. Read `SKILL.md` first to understand triggers, inputs, and workflow steps.
2. Install or copy the skill according to this README.
3. Before using it on real work, run a small example or validation script.

## 入口与元信息 / Entry Points & Metadata

- GitHub 仓库 / Repository: https://github.com/siuserxiaowei/wechat-daily-report-skill
- Live / 在线入口：https://siuserxiaowei.github.io/wechat-daily-report-skill/
- 默认分支 / Default branch: `main`
- 主要语言 / Primary language: `HTML`
- 可见性 / Visibility: `public`
- 仓库类型 / Repository type: `source`
- Topics / 主题：`daily-report`, `jinja2`, `obsidian`, `playwright`, `wechat`, `chat-report`

## 本地运行 / Local Run

```bash
git clone https://github.com/siuserxiaowei/wechat-daily-report-skill.git
cd wechat-daily-report-skill
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## 仓库结构 / Repository Map

| 路径 / Path | 中文说明 | English |
| --- | --- | --- |
| `README.md` | 项目入口说明，先读这里。 | Main project entry point and orientation. |
| `SKILL.md` | Skill 的核心说明、触发条件和执行步骤。 | Core skill instructions, trigger rules, and workflow. |
| `requirements.txt` | Python 依赖列表。 | Python dependency list. |
| `index.html` | 静态站首页或页面入口。 | Static-site homepage or entry page. |
| `assets` | 图片、样式、数据等资源。 | Images, styles, data, and other assets. |
| `docs` | 文档或 GitHub Pages 输出目录。 | Documentation or GitHub Pages output. |
| `scripts` | 构建、同步、生成或维护脚本。 | Build, sync, generation, or maintenance scripts. |
| `examples` | 示例输入、用法或 fixture。 | Examples, usage samples, or fixtures. |
| `LICENSE` | 许可证文件。 | License file. |
| `agents` | Agent 配置或平台适配文件。 | Agent configuration or platform adapters. |
| `references` | 参考资料、规范或补充说明。 | References, specifications, or supporting notes. |
| `reports` | 项目文件或目录。 | Project file or directory. |

## 维护备注 / Maintenance Notes

- 中文：当项目目标、在线入口、运行命令或目录结构变化时，同步更新本说明。
- English: Keep this guide updated when the project purpose, live link, run commands, or structure changes.
- 中文：修改代码、数据或生成页面后，优先运行相关构建、测试或校验命令。
- English: After changing code, data, or generated pages, run the relevant build, test, or validation command.

## 安全与隐私 / Safety & Privacy

- 中文：不要提交 API key、token、密码、cookie、私有链接或内部账号资料。
- English: Do not commit API keys, tokens, passwords, cookies, private URLs, or internal account data.
- 中文：公开 GitHub Pages 前，确认资料已脱敏并允许公开。
- English: Before publishing GitHub Pages output, confirm the material is redacted and cleared for public release.
<!-- SIUSER-REPO-GUIDE:END -->



<!-- SIUSER-SEO-INTRO:START -->

## 项目介绍 / Project Introduction

**中文介绍**：微信群日报 Skill，用本地只读微信数据生成日报、长图和复盘素材，适合社群运营和信息整理。

**English**: A WeChat daily report skill that uses local read-only WeChat data to generate reports, long images, and review materials for community operations.

**SEO 关键词 / SEO Keywords**: WeChat daily report, community operations, AI summary, local data, 微信群日报

<!-- SIUSER-SEO-INTRO:END -->

把微信群聊天记录整理成一份可阅读、可截图、可归档的「群日报」。

这版重点重做了 UI，也把数据入口调整为优先使用 `jackwener/wx-cli`：`wx-cli` 负责从本机微信获取聊天记录，本仓库负责把记录整理成日报 HTML/PNG。

## 预览

![群日报预览](examples/qun-ribao-demo.png)

本仓库内置示例：

- [在线预览](https://siuserxiaowei.github.io/wechat-daily-report-skill/)
- [HTML 预览](examples/qun-ribao-demo.html)
- [PNG 长图](examples/qun-ribao-demo.png)

## 能做到什么

- 生成微信群「每日聊天记录报告」
- 汇总今日话题、资源链接、重要消息、精彩对话、问答、成员输出
- 用聊天气泡还原关键对话，不只是统计数字
- 输出交互式 HTML 和可分享 PNG 长图
- 支持按成员过滤相关内容
- 默认用 `jackwener/wx-cli` 获取本地微信聊天记录
- 可以作为 Obsidian 归档素材：把 HTML/PNG/生成的 Markdown 放进 vault 即可

## 不能误解的地方

这不是 Obsidian 插件，也不是安装后自动打通微信的插件。

它是一个 Skill + 本地脚本工作流：先拿到微信聊天数据，再让 AI 生成结构化日报内容，最后渲染成 HTML/PNG。如果你想在 Obsidian 里长期查看聊天记录、附件和资料，需要再把导出的 Markdown/HTML/图片/附件目录放入 Obsidian vault。

## 数据来源怎么选

不是只能用 WeFlow。

| 方式 | 适合场景 | 说明 |
| --- | --- | --- |
| jackwener/wx-cli | 推荐主路线 | 直接查询本地微信聊天记录，本仓库已内置 `scripts/wx_cli_to_report.py` 适配 |
| 本地 wechat-cli 包 | 备用路线 | 如果装不了 `wx`，可以用你本地的 `wechat-cli` 二进制，通过 `--binary` 指定 |
| 手工导出的聊天文本/JSON | 快速试用 | 直接让 AI 按 `references/ai_prompt.md` 生成 `ai_content.json`，再渲染 |
| WeFlow | 后续扩展 | 适合做更完整的导出、解密、年报、本地 API |
| CipherTalk | 底层参考 | 更适合参考微信数据库解密与读取思路 |
| 旧版本地解密脚本 | 兼容路线 | 仓库仍保留旧脚本，但优先推荐 wx-cli |

更详细说明见 [数据来源说明](docs/data-sources.md)。

## 安装

```bash
git clone https://github.com/siuserxiaowei/wechat-daily-report-skill.git
cd wechat-daily-report-skill
python3 -m pip install -r requirements.txt
python3 -m playwright install chromium
```

安装 `wx-cli`：

```bash
npm install -g @jackwener/wx-cli
```

macOS 首次使用按 `wx-cli` 官方要求初始化：

```bash
codesign --force --deep --sign - /Applications/WeChat.app
killall WeChat && open /Applications/WeChat.app
sudo wx init
wx sessions
```

如果你要作为 Codex/Claude Skill 使用，也可以把仓库放到对应 skills 目录：

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/siuserxiaowei/wechat-daily-report-skill.git ~/.codex/skills/wechat-daily-report-skill
```

## 先跑一遍示例

从 wx-cli JSON 样例生成日报输入：

```bash
python3 scripts/wx_cli_to_report.py \
  --input-json examples/wx_cli_history_sample.json \
  --chatroom "Dont哥 对谈群" \
  --date 2026-04-30 \
  --output-stats examples/wx_stats_from_sample.json \
  --output-text examples/wx_simplified_chat_sample.txt
```

渲染内置完整示例：

```bash
python3 scripts/generate_report.py \
  --stats examples/sample_stats.json \
  --ai-content examples/sample_ai_content.json \
  --output examples/qun-ribao-demo.html
```

生成 PNG 长图：

```bash
python3 scripts/generate_report.py \
  --stats examples/sample_stats.json \
  --ai-content examples/sample_ai_content.json \
  --output examples/qun-ribao-demo.png \
  --viewport-width 1180 \
  --viewport-height 1400 \
  --device-scale-factor 2
```

## 生成真实群日报

### 1. 用 wx-cli 获取微信聊天记录

确认能看到最近会话：

```bash
wx sessions
```

把某个群当天记录转成日报输入：

```bash
python3 scripts/wx_cli_to_report.py \
  --chatroom "群名称或 chatroom id" \
  --date 2026-04-30 \
  --limit 5000 \
  --output-stats stats.json \
  --output-text simplified_chat.txt \
  --raw-output raw_wx_history.json
```

产物：

- `stats.json`：消息数、活跃成员、话唠榜、词云等统计数据
- `simplified_chat.txt`：压缩后的聊天文本，给 AI 生成日报内容用
- `raw_wx_history.json`：原始 wx-cli 输出，便于排查

### 2. 如果只能用本地 wechat-cli 包

你提到的 `wechat-cli-pkg.tar.gz` 也能用。解压后直接把二进制路径传给适配器：

```bash
tar -xzf /path/to/wechat-cli-pkg.tar.gz -C /tmp/wechat-cli-pkg
python3 scripts/wx_cli_to_report.py \
  --binary /tmp/wechat-cli-pkg/wechat-cli-pkg/wechat-cli/node_modules/@canghe_ai/wechat-cli-darwin-arm64/bin/wechat-cli \
  --chatroom "群名称或 chatroom id" \
  --date 2026-04-30 \
  --limit 5000 \
  --output-stats stats.json \
  --output-text simplified_chat.txt
```

### 3. 生成 AI 内容

把下面三个东西一起交给 AI：

- `references/ai_prompt.md`
- `stats.json`
- `simplified_chat.txt`

要求 AI 只输出合法 JSON，保存为：

```text
ai_content.json
```

### 4. 渲染日报

生成交互式网页：

```bash
python3 scripts/generate_report.py \
  --stats stats.json \
  --ai-content ai_content.json \
  --output report.html
```

生成可分享长图：

```bash
python3 scripts/generate_report.py \
  --stats stats.json \
  --ai-content ai_content.json \
  --output report.png \
  --viewport-width 1180 \
  --viewport-height 1400 \
  --device-scale-factor 2
```

## 放进 Obsidian

推荐目录：

```text
YourVault/
  WeChat/
    DailyReports/
      2026-04-30-report.html
      2026-04-30-report.png
      2026-04-30-ai_content.json
      2026-04-30-stats.json
```

你可以在 Obsidian 里新建一篇笔记：

```markdown
# 2026-04-30 群日报

![[2026-04-30-report.png]]

HTML 交互版：[[2026-04-30-report.html]]
```

## 项目结构

```text
assets/report_template.html      # 新版日报 UI 模板
scripts/wx_cli_to_report.py      # wx-cli/wechat-cli 转日报输入
scripts/analyze_chat.py          # 从本地微信数据生成 stats/simplified_chat
scripts/generate_report.py       # Jinja2 渲染 HTML，并用 Playwright 输出 PNG
references/ai_prompt.md          # AI 生成 ai_content.json 的提示词
examples/                        # 示例数据、HTML 和长图截图
docs/data-sources.md             # 数据来源和 WeFlow/CipherTalk 接入说明
SKILL.md                         # 给 Codex/Claude 使用的 Skill 说明
```

## 参考来源

- 首选数据入口：[jackwener/wx-cli](https://github.com/jackwener/wx-cli)
- UI 方向参考：[群日报示例页面](https://simonlin000.github.io/qun-riba-20260430/)
- 原始 skill 思路参考：[ADVISORYDZ/wechat-daily-report-skill](https://github.com/ADVISORYDZ/wechat-daily-report-skill)
- 数据导出方向参考：[hicccc77/WeFlow](https://github.com/hicccc77/WeFlow)
- 微信解密思路参考：[ILoveBingLu/CipherTalk](https://github.com/ILoveBingLu/CipherTalk)

## License

MIT

<!-- SIUSER-CONTACT:START -->

## 联系我 / Contact

想交流 AI 工具、内容自动化、SEO、私域增长或项目合作，可以扫码加我微信。

For collaboration on AI tools, content automation, SEO, private-domain growth, or product experiments, scan the WeChat QR code below.

<img src="https://raw.githubusercontent.com/siuserxiaowei/siuserxiaowei/main/assets/contact/wechat-qrcode.jpg" width="180" alt="WeChat QR code / 微信二维码" />

**关键词 / Keywords**: WeChat daily report, community operations, AI summary, local data, AI tools, AI automation, GitHub Pages, SEO

<!-- SIUSER-CONTACT:END -->
