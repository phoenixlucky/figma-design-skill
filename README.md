<h1 align="center">figma-design-skill</h1>

<p align="center"><b>把 Claude 官方 UI kit 的设计细节取到手，照着它改 / 做软件页面</b><br>
<sub>An agent skill that turns the Claude UI kit into runnable page code — not a design appreciation.</sub></p>

<p align="center">
  <a href="SKILL.md"><img alt="version" src="https://img.shields.io/badge/version-2.4.0-D97757?style=flat-square"></a>
  <a href="LICENSE"><img alt="license" src="https://img.shields.io/badge/license-MIT-2F855A?style=flat-square"></a>
  <a href="SKILL.md"><img alt="skill" src="https://img.shields.io/badge/type-agent%20skill-4B5563?style=flat-square"></a>
  <a href="references/anthropic-mcp-apps-design.md"><img alt="blueprint" src="https://img.shields.io/badge/blueprint-Claude%20UI%20kit-2563EB?style=flat-square"></a>
  <a href="references/browser-recipes.md"><img alt="mcp" src="https://img.shields.io/badge/tooling-Chrome%20MCP-7C3AED?style=flat-square"></a>
</p>

---

一个给 AI 用的**软件界面设计规范** skill，蓝本是 **Claude 官方 UI kit**：把 Claude 的 UI 细节取到手（变量 token、组件几何、动效数值、官方硬规则），照着它**改**现有软件页面，或**做**新页面——交付能落地的代码或逐层改稿方案。

## 三条定位

| # | 定位 | 含义 |
|---|---|---|
| 1 | **蓝本是 Claude** | 颜色 37 / 字体 29 / 几何 15 个变量，加官方指南的九条硬规则，已经取好放在仓库里（[`references/anthropic-mcp-apps-design.md`](references/anthropic-mcp-apps-design.md)），不用再翻一遍 Figma |
| 2 | **交付是页面** | CSS 变量 + 字面量的可运行代码、组件代码，或逐层改稿 diff——不是设计赏析，也不是"看着差不多"的临摹 |
| 3 | **蓝本没覆盖的层要明说** | 官方 UI kit **没有**间距 token、**没有**任何原型动效。要用就写明取自次选蓝本（社区逆向）或标"自定"，不借蓝本的名义写自己的数 |

**当前版本：`2.4.0`** —— 唯一权威出处是 [`SKILL.md`](SKILL.md) frontmatter 的 `version` 字段；改版本号时三处同步，见[维护约定](#维护约定)。

## 目录

- [能拿到什么](#能拿到什么)
- [触发场景](#触发场景)
- [什么是蓝本：它做什么、不做什么](#什么是蓝本它做什么不做什么)
- [两份蓝本](#两份蓝本)
- [工作原理](#工作原理)
- [怎么用](#怎么用)
- [目录结构](#目录结构)
- [安装与同步](#安装与同步)
- [维护约定](#维护约定)
- [License](#license)

## 能拿到什么

| 产出 | 内容 | 用途 |
|---|---|---|
| **页面代码** | 蓝本落成 CSS 变量 + 字面量，关键数值带注释标出处（`border-radius: 6px; /* Border/Radius SM */`） | 直接跑、直接接进项目 |
| **改稿 diff** | 元素 / 现值 / 改成 / 蓝本依据，四列一处改动；密集处附最小代码片段 | 不动结构也能量齐细节 |
| **映射表** | 目标页面维度 / 蓝本取值 / 落到页面的值，三列一页 | 看清对齐了哪些层 |
| **细节表** | 只要细节时给：token 表 / 硬规则 / 蓝本里没有的 | 自己拿去算 |

图标与配图统一放在 `public/assets/` 对应目录。默认用生图工具绘制，裁切为可直接引用的图片资源后收入项目资源库；只有生图不支持或无法满足精度要求时才考虑 SVG。社区逆向的图标尺寸只能作为有来源标注的参考，不属于官方 token。

## 触发场景

- 要按 Claude 的界面风格**做新页面**或**改造现有页面**（配色、字号、圆角、层级、动效对齐）
- 用户贴 `figma.com/design/…`、`figma.com/community/file/…` 链接，要求"提取设计细节 / 规范 / token / 设计理念"
- 用户贴**网页版**设计系统（Storybook 站点、逆向文档 SPA）——取法与 Figma 相反：**源码 > DOM > 截图**
- 要校某个具体数值：圆角阶梯、控件高度、双环阴影、行高节奏、字重、弹簧参数

## 什么是蓝本：它做什么、不做什么

| 做 | 不做 |
|---|---|
| 呈现 Claude 的 token / 组件几何 / 动效数值 / 硬规则 | 不做设计赏析、不评"好不好看" |
| 照着蓝本**改**已有页面、**做**新页面 | 不发明蓝本没有的具体数值（要就标"自定"） |
| 交可运行代码或逐层改稿 diff | 不交"看着差不多"的临摹稿 |
| 官方与社区来源分列、冲突以官方为准 | 不把社区逆向的数字混进官方表里 |

## 两份蓝本

| 文件 | 定位 |
|---|---|
| [`references/anthropic-mcp-apps-design.md`](references/anthropic-mcp-apps-design.md) | **主蓝本**：Claude 官方 UI kit 的全套变量 token、组件 Auto layout 实测、官方指南硬规则 |
| [`references/claude-design-system-storybook.md`](references/claude-design-system-storybook.md) | **次选蓝本**：第三方逆向的 Claude 桌面端。**社区来源，非官方**；只补官方缺的层（像素几何、11 个关键帧、弹簧参数），与官方冲突时以官方为准 |
| [`references/browser-recipes.md`](references/browser-recipes.md) | 可复制的 DOM 选择器与操作序列，**代码口径的权威来源** |

蓝本里有什么，一层一层对着看：

| 层 | 蓝本内容 | 落到页面上是什么 |
|---|---|---|
| 颜色 | 37 个变量，**Light / Dark 双 mode**：Background / Text / Border / Ring | CSS 变量两套 + 主题切换 |
| 字体 | 29 个变量：`Anthropic Sans Text` / `JetBrains Mono`；正文四档 12 / 14 / 16 / 18，行高统一 1.4；标题七档，行高 1.4 → 1.25 → 1.1 → 1.0 | `font-size` / `line-height` 阶梯 |
| 几何 | 15 个变量：桌面圆角 4 / 6 / 8 / 10 / 12 / 999；移动独立梯度 0 / 2 / 4 / 8 / 10 / 14 / 24 / 9999；描边 `0.5` 发丝线 | `border-radius` / `border-width` |
| 间距 | **没有 token**，内嵌在组件 Auto layout 里（如 Inline card：gap 128 / padding 128） | 组件级 gap / padding，别硬造一套 spacing 体系 |
| 动效 | 官方 UI kit **没有任何 prototype 交互** | 要曲线 / 关键帧就取次选蓝本，或自定并标明 |
| 硬规则 | 官方指南的九条（内联卡片、移动端、视觉、动效、字体） | 直接当约束写进页面 |

## 工作原理

```
Figma 文件 / 网页版设计系统
        │
        │  Chrome MCP（无需 Figma 官方 MCP、无需 access token）
        ▼
┌──────────────────────────────────────────────┐
│ 变量面板（DOM 实读）      右侧 Design 面板（实读）│
│ 画布（只能截图，靠视觉读）                      │
└──────────────────────────────────────────────┘
        │
        ▼
   映射表：目标页面维度 ↔ 蓝本取值 ↔ 落到页面的值
        │
        ▼
 页面代码（CSS 变量 + 字面量带注释标出处） / 改稿 diff
```

核心认知是 **Figma 内容分三层，取法完全不同**：

| 层 | 内容 | 能否读 DOM | 取法 |
|---|---|---|---|
| 变量 / 样式 | Variables 面板里的 Border / Colors / Typography 集合 | **能**，是普通 DOM 表格 | CDP 读 `input.value` |
| UI 面板 | 图层面板、右侧 Design / Prototype 面板 | **能**，是普通 DOM | 选中节点后读 `innerText` |
| 画布 | 画布上的图形与文字 | **不能**，画布是 `<canvas>` | 只能截图，靠视觉读 |

> **能读 DOM 的绝不要靠截图猜；画布内容只能截图看。**

## 怎么用

- **AI 侧**：加载本 skill 后按 [`SKILL.md`](SKILL.md) 的「标准流程取蓝本 → 建映射表 → 出代码 / 出改稿」走；取数靠本地 Chrome MCP（`chrome/chrome_page_navigate`、`chrome/chrome_script_execute`、`chrome/chrome_page_screenshot`、`chrome/chrome_page_read_accessibility`、`chrome/chrome_computer_act`）。**不需要 Figma 官方 MCP，也不需要 access token。** 工具名与参数以实时 `tools/list` 为准。
- **人侧**：说清两件事即可——要改 / 要做哪个页面，对齐哪几层（颜色 / 字体 / 几何 / 动效）。
- **降级**：chrome MCP 不可用时，网页源优先 `web_fetch` / `chrome/chrome_page_load_read` 直取源码或正文；只差 token 且用户有 access token 时才是 Figma REST（`/v1/files/:key/variables/local`）；都没有就如实说明缺什么，**不要凭印象编数值**。

## 目录结构

```
SKILL.md                                      # 主文件：拿蓝本 → 建映射表 → 出页面（流程 / 落值口径 / 自检 / 失败降级 / 陷阱清单）
references/anthropic-mcp-apps-design.md       # 主蓝本：Claude 官方 UI kit 的 token、组件实测、硬规则
references/claude-design-system-storybook.md  # 次选蓝本：社区逆向的 Claude 桌面端，补几何与动效
references/browser-recipes.md                 # 可复制的 DOM 选择器与操作序列（代码口径的权威来源）
README.md                                     # 本文件
CHANGELOG.md                                  # 修订记录
LICENSE                                       # MIT
```

## 安装与同步

本仓库是 **skill 的源目录**；AI 实际加载的是全局 skills 根下的**副本**。只改源文件不同步，跑的还是旧版。

```powershell
git clone https://github.com/phoenixlucky/figma-design-skill.git
```

| 项 | 值 |
|---|---|
| 源目录 | 本仓库 clone 到的位置（例：`E:\home\figma-design-skill`） |
| 已安装副本 | `%APPDATA%\reasonix\skills\figma-design-skill\`（`canonicalPath = …\figma-design-skill\SKILL.md`） |
| 技能名 | `figma-design-skill` —— 与 frontmatter `name` 一致 |

改完源文件跑一遍同步；**第 3 步必须全 OK**：

```powershell
$src = '<本仓库路径>'                              # 例：'E:\home\figma-design-skill'
$dst = "$env:APPDATA\reasonix\skills\figma-design-skill"

# 1) 备份现有副本（可回滚）
Copy-Item -Recurse -Force $dst "$env:TEMP\skill-backup-$(Get-Date -Format yyyyMMdd-HHmmss)"

# 2) 镜像覆盖（整目录）
New-Item -ItemType Directory -Force -Path $dst | Out-Null
Copy-Item -Recurse -Force (Join-Path $src '*') $dst

# 3) 校验：逐个文件比对哈希，必须全部 OK
Get-ChildItem $src -Recurse -File | ForEach-Object {
  $rel = $_.FullName.Substring($src.Length + 1)
  $a = (Get-FileHash $_.FullName).Hash
  $b = (Get-FileHash (Join-Path $dst $rel) -ErrorAction SilentlyContinue).Hash
  if ($a -eq $b) { "OK       $rel" } else { "MISMATCH $rel" }
}
```

首次安装、或要清理注册信息时，走 `install-capability` skill 的 `install_source`：

- **安装**：`source=<本仓库路径>`、`kind=skill`、`scope=global`；先 `apply=false` 拿 `planId`，再用**同一个 `planId`** `apply=true`。
- **卸载**：`op=uninstall`、`name=<技能目录名>`、`scope=global` —— `scope` 必须与安装时一致；`replace=true` 对 skill **无效**，别拿它当"覆盖安装"用。
- 装完别只看返回的 `canonicalPath`：同名副本可能来自更近的作用域，要按上面的哈希核对。

## 维护约定

1. **新产出按新文件追加到 `references/`，不改写既有产出** —— 既有的两份蓝本是页面落值时的对照物。
2. **每份产出末尾留「方法论教训」节**：把这次踩到的坑沉淀成 `SKILL.md` 里的新陷阱或降级路径，而不是只留结论。
3. **官方与社区逆源的数值不得混在同一张表里**：社区来源的项要标出来源属性，与官方冲突时以官方为准。
4. **改工具名 / 选择器要三处同步**：`SKILL.md`、`references/browser-recipes.md`、产出文件里的操作记录；工具名以实时 `tools/list` 为准（本文档引用的 chrome 工具已对照本地 `chrome` MCP server 的真实工具表核验存在，上游升级后需重新核验）。
5. **版本号三处同步**：`SKILL.md` frontmatter 的 `version`（权威）、`README.md` 的「当前版本」、`CHANGELOG.md` 的版本小节标题。只改一处会出现"文档说 A、加载器读 B"的分叉；改完照上面的同步脚本覆盖副本并校验哈希。

## License

[MIT](LICENSE) © 2026 phoenixlucky
