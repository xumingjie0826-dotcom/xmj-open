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
| 04 | last30days-skill | [mvanhorn/last30days-skill](https://github.com/mvanhorn/last30days-skill) | 按真人互动信号排名的人物/公司/话题调研引擎 | 高（海外向） | 中（中文源仅小红书） | 中 | 已收藏 |

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

## 04 · last30days-skill

| 字段 | 内容 |
|------|------|
| 仓库 | https://github.com/mvanhorn/last30days-skill |
| 协议 / 版本 | MIT · v4.4.0 · 约 69MB · 曾登 GitHub Trending 当日第 1 |
| 一句话 | 「按真人互动信号排名」的研究引擎：并行搜 Reddit / X / YouTube / TikTok / HN / Polymarket / GitHub，外加专利、招聘等，再由 LLM 汇总成一份简报。 |
| 价值 | 高（做人物/公司/话题调研时）。卖点是「搜的是人不是编辑」。 |
| 可用性 | 中。Claude Code 走 plugin marketplace；Codex/Cursor/Copilot/Gemini 等 50+ Agent Skills 宿主走 `npx skills add … -g`；另有 MCP server。默认零配置即可用 Reddit/HN/Polymarket/GitHub；完整能力需自备各平台 key/CLI。Trae 未点名，走 Agentskills / MCP 路线。 |
| 中文支持 | **很有限**：唯一的中文平台是**小红书**，且要本机跑 `x-mcp` 浏览器插件或 `xiaohongshu-mcp` 服务、用 `--search xhs` 显式请求。**没有**微信 / 微博 / 知乎 / B站 / 抖音国内版 / 雪球 / 东方财富 / 今日头条。 |
| 风险 | 中（能力大、触点多，但文档极其完整、开关齐全）。要点：会把你填的 topic 发给多个第三方服务；可读取浏览器 cookie（默认关，需明确同意）；会安装外部 CLI（npx 包 / yt-dlp 等）；默认**无遥测**。 |
| 状态 | 已收藏 |

**安装**
```bash
# Claude Code
/plugin marketplace add mvanhorn/last30days-skill
/plugin install last30days
# 其他 Agentskills 宿主（Codex/Cursor/Copilot/Gemini…）
npx skills add mvanhorn/last30days-skill -g
```

**使用**
```
/last30days <人物名 / 公司名 / 话题>      # 例：/last30days Peter Steinberger
```
首跑会弹配置向导，30 秒内解锁 X / YouTube / TikTok / arXiv 等更多来源。

**注意**
- 是「研究工具」不是「搜索框」：输出的是一份综合简报，耗 token、耗时间。
- 注意数据外发范围：topic 会送到所有启用的来源；想要纯本地重排，就别配 Gemini/OpenAI/xAI/OpenRouter 的 key。
- **对你的用途（个人工作台里的"公司讯息 + 行业知识"汇总）**：**不太适合**。它的强项是英文/海外的人物与公司调研，中文源基本缺失（只有小红书）；中文公司/行业资料建议另找中文源方案。

---
<!-- 后续条目：复制上面的分节模板，编号 ++，并在顶部索引表加一行 -->
