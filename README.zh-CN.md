# grain — 面向 AI 代理的 UX 评审技能

> 顺着真实用户思考、阅读、决策、信任和恢复的方式工作。

**语言:** [English](README.md) | [한국어](README.ko.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [Español](README.es.md)

由 [Pango Gy](https://pango-gy.com) 维护。

`grain` 是一个可移植的 AI 代理技能，用于评审和塑造面向用户的产品决策。它不是视觉主题、组件库或设计系统。它是一个 UX 判断层：当流程、表单、错误状态、AI 动作、权限提示或按钮文案违背真实用户的使用方式时，它会提出反对意见。

可以把它和前端生成器、设计系统技能、UI 套件、产品代码评审一起使用。那些工具帮助代理构建界面；`grain` 帮助代理判断这个界面是否尊重用户的努力、注意力、可访问性、信任和恢复路径。

## 安装

```bash
npx skills add pango-gy/grain-ux-skill
```

安装器会检测支持的 AI 工具，并在每个工具中创建 `grain`。再次运行同一命令即可更新。

删除:

```bash
npx skills remove grain
```

## 触发场景

`grain` 会在涉及用户体验的决策中自动启用。

- 编写、重构或评审 UI 组件、页面、表单和流程
- 设计或评审空状态、加载、失败、部分成功、离线和权限拒绝状态
- 编写文案、标签、微文案、错误消息、引导流程或通知
- 检查可访问性、键盘行为、焦点顺序、触摸目标、动效和响应式行为
- 设计表单、导入、筛选器、设置、权限、共享、计费、AI 输出或自动化
- 评审截图、原型、仪表盘、内部工具、管理界面或 SaaS 工作流

对于纯后端逻辑、基础设施，或没有用户可见行为的工作，它应该保持安静。

## 覆盖范围

七个领域，一个判断口径：

- **用户流程与信息架构** — 先考虑路径，再考虑页面；先考虑任务，再考虑表格。
- **认知负荷与简洁性** — 减少决策，而不只是减少点击。
- **表单与输入** — 每个字段都有成本，校验应该帮助用户，而不是责备用户。
- **可访问性与包容性交互** — 键盘、触摸、焦点、动效、对比度和视口都是基础 UX。
- **信任、同意与用户掌控感** — 避免意外发送、共享、扣费、删除、AI 提交或自动化执行。
- **错误、边界情况与恢复** — 空/加载/失败/离线状态都是产品的一部分。
- **微文案与语气** — 按钮描述结果，错误不责备用户，每句话都应该能自然读出口。

每个领域的详细参考位于 [`skill/references/`](skill/references)。`SKILL.md` 会告诉代理什么时候加载哪个参考文件，从而让主技能保持聚焦。

## 核心理念

`grain` 会优先应用这些原则：

- 让下一步行动显而易见。
- 保留用户已经付出的努力。
- 不让用户感到意外。
- 不只是要求确认，而是提供撤销。
- 把可访问性当作基础 UX，而不是特殊模式。
- 把失败状态作为产品的一部分来设计。

完整原则、领域路由和反模式在 [`skill/SKILL.md`](skill/SKILL.md) 中。

## 定位

`grain` 最适合作为 companion skill 使用：

- 搭配**前端生成器**，在代码合入前发现 UX 回退。
- 搭配**设计系统**，确认组件不仅样式正确，也用于正确的任务。
- 搭配 **AI/自动化工具技能**，在持久化或对外部产生影响的操作前要求 preview、consent、status、history 和 explicit approval。
- 搭配**产品评审流程**，把模糊反馈转化为具体原则和反模式。

它不会生成视觉识别、选择品牌配色，也不会替代产品研究。它为代理在编码和评审时已经在做的决策提供可复用的 UX 标准。

## 评审提示示例

```text
Use grain to review this checkout flow for trust, consent, and recovery.
```

```text
Use grain while refactoring this settings form. Preserve input and improve validation UX.
```

```text
Use grain to check whether this AI-generated email flow needs preview, edit, and approval states.
```

```text
Use grain to review this dashboard for cognitive load, accessibility, and empty states.
```

## 作者

Pango Gy CTO 유승재 ([pinkyooysj@pango-gy.com](mailto:pinkyooysj@pango-gy.com))

公司: [Pango Gy](https://pango-gy.com)

## 许可证

[MIT](LICENSE)。你可以使用、fork，或用自己的语气重写它。目标是让更多产品把 UX 当作一等公民。

## 思想来源

它站在 Donald Norman、Jakob Nielsen、Steve Krug、Bruce Tognazzini、Alan Cooper、Dan Saffer 和 Edward Tufte 的思想之上。每个思想的来源可参考 [`skill/SKILL.md`](skill/SKILL.md) 中的 `Lineage` 部分。
