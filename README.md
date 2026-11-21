# Skill 收藏清单

> 从 GitHub 搜集的 skill 评估记录：能不能用、怎么装、怎么用、有无风险。
> 换电脑 `git clone` 本仓库即可拿到。

## 怎么读这份文件

- **顶部索引表**：一眼看全，用来快速定位/对比。
- **正文按 `NN · 名称` 编号分节**：编号与索引表一一对应；每个 skill 的字段顺序完全一致，所以「哪段介绍属于哪个 skill」不会混。
- 状态：`已收藏` / `评估中` / `不推荐`

## 索引

| # | 名称 | 仓库 | 一句话 | 价值 | 可用性 | 风险 | 状态 |
|---|------|------|--------|------|--------|------|------|
| 01 | huashu-design（花叔Design） | [alchaincyf/huashu-design](https://github.com/alchaincyf/huashu-design) | HTML 原生设计 skill（原型/deck/动效/信息图等） | 高 | 基础版即可用 | 低 | 已收藏 |
| 02 | plannotator | [backnotprop/plannotator](https://github.com/backnotprop/plannotator) | 给 AI 编码 agent 的本地批注/审阅界面（计划/diff/PR） | 高 | 中（未官方支持 Trae） | 中 | 已收藏 |
| 03 | vibe-knowledge-film | [HeyChengC/vibe-knowledge-film](https://github.com/HeyChengC/vibe-knowledge-film) | 代码直出「无旁白」知识短片（抖音 Vibe 知识大赏风） | 高（科普向） | 中（需 Chrome/ffmpeg） | 低 | 已收藏 |
| 04 | claude-mem | [thedotmack/claude-mem](https://github.com/thedotmack/claude-mem) | 给 AI coding agent 的持久记忆：跨会话不忘事 | 高（重度用 agent） | 中（未点名 Trae） | 中 | 已收藏 |

---

## 01 · huashu-design（花叔Design）

| 字段 | 内容 |
|------|------|
| 仓库 | https://github.com/alchaincyf/huashu-design |
| 协议 / 版本 | MIT · v3.4.2 · 42MB（多为素材） |
| 一句话 | HTML 原生设计 skill，做高保真原型 / 幻灯片 / 动画视频 / 信息图 / 小红书图文 / App Store 宣传图，含「三方向初稿」「品牌资产协议」「打磨环」「6 维度评审」等机制。 |
| 价值 | 高。生产级工作流，非普通 prompt 技巧。 |
| 可用性 | **基础版（只产出 HTML）现在就能用、零依赖**；完整版需装 Python3/Node/ffmpeg/playwright + 生图 key，暂缓。 |
| 风险 | 低（核心流程本地零联网；云功能仅火山/字节/OpenAI，需自带 key 且有 `--yes` 闸门）。 |
| 状态 | 已收藏 |

**安装**（装完务必自检目录含 references/ assets/ scripts/ demos/）
```bash
npx skills add alchaincyf/huashu-design
# 或
git clone https://github.com/alchaincyf/huashu-design.git <你的skills目录>/huashu-design
```

**使用**（直接自然语言，无面板/按钮）
```
「做一份 AI 心理学的演讲 PPT，推荐 3 个风格方向让我选」
「做个 AI 番茄钟 iOS 原型，4 个核心屏幕要真能点击」
「把这段逻辑做成 60 秒动画，导出 MP4 和 GIF」
「帮我对这个设计做一个 6 维度评审」
```

**注意**
- 不能只拷 SKILL.md，要整包安装。
- 会在 `~/.huashu-design/` 写本地记忆（口味原话 + 项目绝对路径），不上传；可设 `HUASHU_DESIGN_HOME` 改位置或删目录。
- 偶发 `git ls-remote` 查版本，可写 `off` 关闭。

---
## 02 · plannotator

| 字段 | 内容 |
|------|------|
| 仓库 | https://github.com/backnotprop/plannotator |
| 协议 / 版本 | MIT OR Apache-2.0 · v0.29.1 · 约 200MB（是完整 monorepo 产品，不是小 skill） |
| 一句话 | 给 AI 编码 agent 用的本地浏览器「审阅/批注」界面：批注计划、spec、markdown、HTML、diff/PR，反馈直接回传给 agent；另有 Inbox（多 agent 消息台）和终端版。 |
| 价值 | 高（对重度使用 coding agent 的人）。把「看计划 / 看 diff / 提反馈」从终端搬到可视化界面。 |
| 可用性 | 中。官方支持 Claude Code / Codex / Gemini CLI / OpenCode / Kiro / Droid / Amp / **DeepSeek Harness** / Copilot CLI / Pi，**未列 Trae**。在 Trae 里只能走 CLI（`plannotator annotate`、`plannotator review`）或 inbox 的 MCP 通道，属「能用但要手动接」，需装其独立二进制。 |
| 风险 | 中。① `curl \| bash` 第三方安装器 + 从 GitHub Releases 下载二进制；② **默认开启匿名遥测**（每天 ping，无 IP/无 ID，可用 `NO_ANON_PING` 关闭，无界面开关）；③ 分享功能会上传到其服务器（加密、7 天过期，`PLANNOTATOR_SHARE=disabled` 可关）。安全建设规范（SHA256 / SLSA 溯源 / SBOM / Grype）。 |
| 状态 | 评估中 |

**安装**
```bash
curl -fsSL https://plannotator.ai/install.sh | bash      # 装二进制 + 自动配置各 agent（不含 Trae）
# 只要二进制、不要任何 agent 配置：
curl -fsSL https://plannotator.ai/install.sh | bash -s -- --minimal
```

**使用**
```
/plannotator-annotate README.md          # 批注本地 markdown
/plannotator-review                      # 审阅未提交改动
/plannotator-review <PR-URL>             # 审阅 GitHub PR
plannotator annotate http://localhost:5173   # 批注本地运行中的站点
plannotator inbox                        # 多 agent 消息台
```
（Codex 里换成 `!plannotator …` 或 `$plannotator-*` skill）

**注意**
- Trae 不在官方支持列表；最可行的接入是 CLI，或 `plannotator inbox mcp`（MCP 通道，任意 agent 可接）。
- 默认匿名遥测无界面开关，需环境变量 `NO_ANON_PING` 关闭。
- 安装器是 `curl | bash` 且下载预编译二进制，属主要风险面；介意可跳过或自行校验 release 校验和。

---

## 03 · vibe-knowledge-film

| 字段 | 内容 |
|------|------|
| 仓库 | https://github.com/HeyChengC/vibe-knowledge-film |
| 协议 / 版本 | MIT（引擎/脚本/文档）· 约 93MB |
| 一句话 | 做「抖音 Vibe 知识大赏」式的**无旁白知识短片**（2–5 分钟、16:9）：观众读底部字幕，同时看屏上把这句话演出来。全片由代码逐帧画出（Canvas + seek(t) + Playwright + ffmpeg）。 |
| 价值 | 高（面向做科普/知识短片的人），题材很垂直；对不做视频的人用不上。 |
| 可用性 | 中。需 Python3 + playwright + 本机 Google Chrome + ffmpeg；把这整个目录放进 agent 的 skills 目录即可，非 Trae 专属。渲染链较重（逐帧截图再压片）。 |
| 风险 | 低。纯本地渲染，无遥测；唯一联网是 `get_fonts.py` 从 Google Fonts 官方 raw 拉取开源字体。**版权提醒**：作者明确说 `references/analysis.md`、`references/prompts.md` 与 `examples/stim_B`、`info_C` 用了他人短片的字幕/画面设计，属学习对照，不要当自己作品发布。 |
| 状态 | 已收藏 |

**安装**
```bash
pip install -r requirements.txt
python -m playwright install
python engine/get_fonts.py     # 下载开源字体（仓库不含字体）
```

**使用**（把整份文案或一个选题丢给它；它自己选画风、写字幕稿、排分镜表、建工程，先出 30 秒样片再铺全片）
```bash
python scripts/new_film.py <工程目录> --world C   # C=夜曲（讲底层知识） / B=寓言
python engine/render.py <工程目录> --serve        # 浏览器预览
python engine/render.py <工程目录> --sheet 3 8 15 22   # 指定时刻拼图自查
```

**注意**
- 两种画风：`C 夜曲`（抽象/看不见的机制）、`B 寓言`（心理/行为机制）。
- 依赖本机 Chrome，不是自带浏览器。

---

## 04 · claude-mem

| 字段 | 内容 |
|------|------|
| 仓库 | https://github.com/thedotmack/claude-mem |
| 协议 / 版本 | Apache-2.0 · v16.0.2 · 约 108MB |
| 一句话 | 给 AI coding agent 的**持久记忆**：它在旁边跑一个「观察员」agent 边干活边记笔记，下次会话开场就带着上次的记忆。 |
| 价值 | 高（对重度使用 coding agent 的人）。直接解决「agent 每次开新会话都失忆」的痛点。 |
| 可用性 | 中。需 Node `^20.19 || >=22.12`，会自动装 Bun；向量检索用 uv。`npx claude-mem install` 会扫描本机已装的 agent 让你勾选。官方点名 Claude Code / Codex / Cursor / OpenCode + 11 个（Copilot CLI / Goose / Roo / Warp / Zed 仅能查记忆，会话不被记录）；**未点名 Trae**，但有大量宿主适配 + MCP。 |
| 风险 | 中。① 默认开启**匿名分析**（`npx claude-mem telemetry disable` 可关）；② 记忆存本机 `~/.claude-mem`，云同步为 opt-in；③ 默认引导「claude-mem observer」，30 天试用后需订阅（也可改用自备 OpenRouter/Gemini key 或 Anthropic plan）；④ 它会**记录你的会话内容**；⑤ 自动安装 Bun / uv 运行时。 |
| 状态 | 已收藏 |

**安装**
```bash
npx claude-mem install          # 交互式：自动发现本机 agent，让你勾选要接哪些
# 或在 Claude Code 里：
/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem
```
不想接账号：加 `--provider openrouter`（或 gemini），或设 `CLAUDE_MEM_ONLINE_OPTIN=false`；非交互环境：`npx claude-mem install --setup defer`。

**注意**
- `npm install -g claude-mem` 只装 SDK，**不会注册插件钩子**，别用这条。
- 想省 token/省心：可在设置里关掉匿名分析、云同步，改用自备 key 当记忆 provider。
- Trae 未点名，接入要自己试 MCP 或看它是否有 Agentskills 装法。

---
<!-- 后续条目：复制上面的分节模板，编号 ++，并在顶部索引表加一行 -->
