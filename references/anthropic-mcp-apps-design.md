# 主蓝本：Claude 官方 UI kit（Anthropic「MCP Apps for Claude」）

照 Claude 的 UI 细节改 / 做页面时，**取值以本文件为准**：数值来自变量面板 DOM 实读，规则条目来自官方指南原文。

## 来源

| 项 | 值 |
|---|---|
| Figma 文件 | `MCP Apps for Claude (Community)`，file key `fboETg7aUHxMZmXXTNRbjq` |
| Community 页 | https://www.figma.com/community/file/1597641111449594397/mcp-apps-for-claude |
| 提取用链接 | `https://www.figma.com/design/fboETg7aUHxMZmXXTNRbjq/MCP-Apps-for-Claude--Community-?node-id=849-19283&view=variables` |
| 官方指南 | https://claude.com/docs/connectors/building/mcp-apps/design-guidelines （`.md` 后缀可取纯文本） |
| Figma 变量实读日期 | 2026-10-14 |
| 官方在线指南复核日期 | 2026-10-15 |
| 提取方式 | 本地 Chrome MCP：读变量面板 DOM + 截图看画布 |

文件共 **3 个变量集合**（Border 15 / Colors 37 / Typography 29）和 **14 个页面**：
`🖼️ Cover` · `Foundations`(空分隔页) · `🖌️ Color` · `🔠 Typography` · `📐 Layout` · `🖋️ Icons` · `Displays`(空分隔页) · `⬜️ Inline card` · `🎠 Inline carousel` · `↔ Full screen` · `Claude Components`(空分隔页) · `🖥️ Desktop web components` · `📱 Mobile components` · `📣 Promotional assets`

---

## Typography（29 个变量，**单一 mode，没有暗色分支**）

| 组 | 变量 | 值 |
|---|---|---|
| Font | Sans | `Anthropic Sans Text` |
| Font | Mono | `JetBrains Mono` |
| Weight | Normal / Medium / Semibold / Bold | `400` / `500` / `600` / `700` |
| **Weight Mobile** | Medium | **`550`** |
| Size Text | xs / sm / md / lg | 12 / 14 / 16 / 18 |
| Size Heading | xs / sm / md / lg / xl / 2xl / 3xl | 12 / 14 / 16 / 20 / 24 / 28 / 36 |
| Line height Text | xs / sm / md / lg | 16.8 / 19.6 / 22.4 / 25 |
| Line height Heading | xs / sm / md / lg / xl / 2xl / 3xl | 16.8 / 19.6 / 22.4 / 25 / 30 / 30.8 / 36 |

行高写的是 px 不是倍数。上表是**面板实读值**，倍数是**换算值（推算，非实读）**：

| 字号档 | 12 | 14 | 16 | 18 | 20 | 24 | 28 | 36 |
|---|---|---|---|---|---|---|---|---|
| Text 行高 | 16.8 (1.40) | 19.6 (1.40) | 22.4 (1.40) | 25 (≈1.39) | — | — | — | — |
| Heading 行高 | 16.8 (1.40) | 19.6 (1.40) | 22.4 (1.40) | — | 25 (1.25) | 30 (1.25) | 30.8 (1.10) | 36 (1.00) |

节奏是：**正文四档统一 1.4**；标题随字号增大逐档收紧 **1.4 → 1.25 → 1.1 → 1.0**。Text lg 的 `25` 是 `18 × 1.4 = 25.2` 在面板里的取整显示，别当成独立的一档比例。

**Weight Mobile / Medium = 550** 是整套 token 里唯一非标准字重，含义是**跨设备**补偿（移动端比桌面 Medium 500 更重），不是明暗模式补偿。

## Border（15 个变量，单一 mode）

| 组 | 变量 | 值 |
|---|---|---|
| Radius（桌面） | XS / SM / MD / LG / XL / Full | 4 / 6 / 8 / 10 / 12 / 999 |
| **Radius / Mobile** | None / XXS / XS / Small / Medium / Large / XL / Full | 0 / 2 / 4 / 8 / 10 / 14 / 24 / 9999 |
| Width | Regular | **`0.5`**（唯一一个值，发丝线） |

移动端半径是**独立梯度**（更细的档位、更小的起步），且 Full 用 9999 而非 999。

## Colors（37 个变量，**Light / Dark 双 mode**）

格式：`Light → Dark`，带 `%` 的是透明度。色值是**面板原样输出（裸 hex，不带 `#`）**，引用时补 `#` 即可。

**Background**

| 变量 | Light | Dark |
|---|---|---|
| Primary | `FFFFFF` | `30302E` |
| Secondary | `F5F4ED` | `262624` |
| Tertiary | `FAF9F5` | `141413` |
| Inverse | `141413` | `FAF9F5` |
| Ghost | `FFFFFF` 0% | `30302E` 0% |
| Info | `D6E4F6` | `253E5F` |
| Danger | `B53333` | `DD5353` |
| Success | `E9F1DC` | `1B4614` |
| Warning | `F6EEDF` | `483A0F` |
| Disabled | `FFFFFF` 50% | `30302E` 50% |

**Text**

| 变量 | Light | Dark |
|---|---|---|
| Primary | `141413` | `FAF9F5` |
| Secondary | `3D3D3A` | `C2C0B6` |
| Tertiary | `73726C` | `9C9A92` |
| Inverse | `FFFFFF` | `141413` |
| Info | `3266AD` | `80AADD` |
| Danger | `7F2C28` | `EE8884` |
| Success | `265B19` | `7AB948` |
| Warning | `5A4815` | `D1A041` |
| Disabled | `141413` 50% | `FAF9F5` 50% |
| Ghost | `73726C` 50% | `9C9A92` 50% |

**Border** — 全部靠透明度分层，不用实色

| 变量 | Light | Dark |
|---|---|---|
| Primary | `1F1E1D` 40% | `DEDCD1` 40% |
| Secondary | 30% | 30% |
| Tertiary | 15% | 15% |
| Inverse | `FFFFFF` 30% | `141413` 15% |
| Ghost | 0% | 0% |
| Info | `4682D5` | `4682D5` |
| Danger | `A73D39` | `CD5C58` |
| Success | `437426` | `599130` |
| Warning | `805C1F` | `A87829` |
| Disabled | 10% | 10% |

**Ring**（焦点环）

| 变量 | Light | Dark |
|---|---|---|
| Primary | `141413` 70% | `FAF9F5` 70% |
| Secondary | `3D3D3A` 70% | `C2C0B6` 70% |
| Inverse | `FFFFFF` 70% | `141413` 70% |
| Info | `3266AD` 50% | `80AADD` 50% |
| Danger | `A73D39` 50% | `CD5C58` 50% |
| Success | `437426` 50% | `599130` 50% |
| Warning | `805C1F` 50% | `A87829` 50% |

**注意：这套 kit 没有 spacing / gap token**，间距内嵌在组件的 Auto layout 里，不要把它当完整 token 集用。

## 组件层实测

选中 `Inline card / Desktop web` 这个 frame 后，右侧 Design 面板读到：

| 属性 | 值 |
|---|---|
| Auto layout Flow | 横向 |
| Resizing | `W 7968 Hug` / `H 2813 Hug`（**Hug = 内容吸附**，非固定尺寸） |
| Gap | `128` |
| Padding | `128` / `128` |
| Clip content | ✓ |

页面结构上，`⬜️ Inline card` 页包含 `Inline card / Desktop web`、`Inline card / Mobile`、`Shimmers / Mobile` 三组，每组都做 **light / dark 两套**，另有独立的 `Skeleton` 组。

## 原型 / 动效层：**没有**

- `Prototype` 标签下，`Prototype settings` 显示 `Device: No device`
- 右侧停在 `Creating a connection` / `Running your prototype` 帮助态（空态文案）
- 画布上没有任何交互连线

→ 该文件**没有定义任何 prototype 交互**，因此不存在 smart animate 的 easing、时长、贝塞尔曲线可提取。它是 UI kit（组件 + 变量），不是原型 demo。

官方文档里能对应"过渡"的只有三条定性规则（见下），没有曲线数值。

## 官方指南里的硬规则

来自 `design-guidelines.md`：

**内联卡片**
- 高度自适应内容，**禁止嵌套滚动**
- 最多 2 个操作，放卡片底部
- 最多 4–5 个数据点
- 不要 drill-in、面包屑、多视图
- **禁用 menu / popover**（会被容器边界裁切、与宿主 UI 抢 z-index）→ 只用可见控件（segmented button、toggle、inline options）

**移动端**
- 点击目标 ≥ **44pt**
- Inline Card 在对话中按可用宽度铺满，不产生横向溢出；横向浏览使用 Inline Carousel，不能把 Carousel 规则误套到 Inline Card
- 尊重 `hostContext.safeAreaInsets.{top,right,bottom,left}`（px 值），作为根容器 padding 或滚动容器的 `scroll-padding`
- 内联 app 的垂直滚动手势交给会话滚动，别自己抢
- 需要独立纵向滚动区就请求 fullscreen，而不是内联
- `_meta.ui.prefersBorder`：不设时 web 无边框、mobile 有边框；无边框模式要自己扛 safeArea

**Inline Carousel 与 Fullscreen**
- Carousel 用于可比较项目，3–8 项；每卡片含图像、标题、最多三行元数据和可选的一个 CTA；尺寸、视觉层级一致；移动端可横向滑动并露出下一卡边缘。
- Fullscreen 用于需要更大空间的复杂任务；App 提供进入按钮，宿主标题栏提供关闭；聊天输入保持可用；用可折叠侧栏、标签或分页代替浮动面板。
- 在 `ui/initialize` 声明实际支持的 `inline`、`fullscreen`、`pip` 模式；通过 `ui/request-display-mode` 请求切换。
- 移动端 App 填满宿主容器宽度，从 320px 起响应；使用容器查询与 `hostContext`，不要依赖固定 viewport 断点。安全区在 Web / 桌面也可能因宿主输入框覆盖而需要考虑。

**视觉**
- **只用三级字号 + 两档字重（regular / emphasized）**
- 结构性元素（背景、文字、边框、图标）一律用宿主 token，**不硬编码颜色**；只允许在 accent / 品牌色上表达自己
- 明暗两套都要测；宿主 token 自动适配
- 图标用单色描边并匹配宿主图标颜色；图标辅助理解，不承载唯一信息。
- 保持宽松且有逻辑的间距；官方指南给的是定性原则，不提供数值 spacing token。
- 满足 WCAG AA 对比，支持键盘操作，为视觉信息提供文本替代，并用辅助技术检查。

**动效/加载**
- 内联卡片展开到全屏用平滑过渡，且要有明确的可展开提示
- 关闭全屏回到会话时保持原滚动位置
- 加载用 **skeleton**（且结构要贴合最终内容），**不要用 spinner**

**字体**
- Figma 文件用 Anthropic Sans / Anthropic Serif；运行时宿主通过 style variables 提供 Anthropic Sans

**交互边界与安全**
- 直接操作已展示内容（筛选、排序、选择、展开、执行已准备动作）属于 App；自由文本、追问、修改请求和跨主题导航使用 Claude 对话输入。
- 外部 origin 默认阻止；仅通过 `_meta.ui.csp` 声明需要的连接、资源或基础 URI 域。`frameDomains` 对第三方 iframe 有额外安全审查限制。

## 官方来源差异（2026-10-15 复核）

当前 Anthropic 在线指南与 2026-10-14 实读的 Figma Community UI kit 在若干 token 名和值上并不一致。两者都要保留各自来源，不将表格拼成一份“统一官方值”：

| 维度 | Figma UI kit 实读 | 当前在线指南 | 使用口径 |
|---|---|---|---|
| Text LG | 18px；行高 25px | 20px；行高 1.25 | 按目标运行时选择对应来源；不要把一个来源的字号与另一个来源的行高拼接 |
| Mono 字体 | JetBrains Mono | `ui-monospace, monospace` | 设计文件字体与宿主运行时 token 分列 |
| Danger 背景 | `#B53333` / `#DD5353` | `#F7ECEC` / `#602A28` | 语义 token 同名不保证颜色相同；以对应运行时宿主变量为准 |
| 间距 | 没有数字化 spacing / gap 变量；组件 Auto layout 可实读间距 | 只给“留白充足、分组有逻辑”的定性原则 | 不虚构官方 spacing token；从具体组件或目标项目取值 |

内嵌 App 必须优先消费 Claude 运行时传入的 style variables；本地 Figma 变量适合核对设计文件，不得覆盖运行时 token 的适配职责。

---

## 方法论教训

1. **变量面板是取值的唯一权威**。数值读 `input.value`，别靠截图目测；一行里 `input` 的数量决定它有几种 mode。
2. **别把 radius 表当成完整 token 集**：这套 kit 没有 spacing / gap token，间距只在组件的 Auto layout 里。
3. **文件里没有的层要明说**：没有 prototype，就没有曲线、时长、贝塞尔曲线可抄；要动效只能取次选蓝本（`claude-design-system-storybook.md`）或自定并标明。
4. **落到页面上的每个数值都要指得回本文件某一行**；指不出来就标"自定"，不要借蓝本的名义写自己的数。
