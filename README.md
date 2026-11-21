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
<!-- 后续条目：复制上面的分节模板，编号 ++，并在顶部索引表加一行 -->
