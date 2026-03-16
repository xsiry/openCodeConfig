# OpenCode 本地 AGENTS 约定

## 定位

- `AGENTS.md` 只保留稳定、长期有效的本地协作规则，不再充当 OpenCode / Oh-My-OpenCode 的配置快照或 schema 摘录。
- 精确字段、默认值、支持项、版本差异，以运行时工具与官方文档为准：
  - OpenCode: `https://opencode.ai/docs/config/`、`https://opencode.ai/config.json`
  - Oh-My-OpenCode: 官方 GitHub Repo / Releases / 对应版本 schema
- 当 `AGENTS.md` 与运行时工具定义冲突时，以当前工具定义和实际返回为准。

## 本地固定偏好

- Thinking 使用中文；面向用户的回复默认使用简体中文。
- 文件统一使用 UTF-8；除非文件本身已使用其他字符集，否则不要引入 GBK / ANSI。
- 优先使用官方来源；`ohmyopencode.com` 之类非官方站点不能作为规范依据。
- 优先复用仓库现有实现、命名、结构和约定，不为了“更优雅”主动偏离项目风格。

## 配置维护原则

- `~/.config/opencode/opencode.jsonc` 和 `~/.config/opencode/oh-my-opencode.jsonc` 才是本地配置事实来源；`AGENTS.md` 不重复列出完整插件、MCP、agent、category、skill、model 清单。
- 只有“运行时不容易直接看出来、但会持续影响协作质量”的规则才写进 `AGENTS.md`。
- 需要记录配置行为时，优先写“判断原则”和“核对入口”，不要写大段字段镜像。
- 避免在 `AGENTS.md` 中写死“本机当前版本是 X.Y.Z”这类观察值；这类信息很快过期。
- 若确实需要提某个版本差异，必须同时说明适用范围和官方依据；差异失效后应立即删除。

## 建议保留在 AGENTS 的内容

- 语言、编码、来源优先级等本地长期偏好。
- 任务执行时的稳定质量要求：先查现有模式、优先最小安全改动、给出验证证据。
- 本地特有的工作习惯，例如优先使用哪些工具类型、哪些验证命令最可信。

## 不应继续写进 AGENTS 的内容

- OpenCode / Oh-My-OpenCode 的完整 category、skill、tool、MCP 表格。
- schema 已能直接表达的字段清单、默认值、顶层键说明。
- 很容易漂移的版本观察、旧版兼容说明、单次排障笔记。
- 与系统提示或插件提示明显重复的大段通用执行守则。

## 本地工具选择偏好

- 结构化代码分析优先 `serena`，其次 `lsp_*`，最后才是纯文本搜索。
- 小范围精确修改优先 `apply_patch`；大文件或分散改动优先 `morph_edit`。
- 需要验证 OpenCode 配置时，优先查看官方 config docs / schema 与本地 `opencode.jsonc`。
- 需要验证 Oh-My-OpenCode 配置时，优先看对应版本 schema、GitHub Release，以及 `bunx oh-my-opencode doctor --json` / `--verbose`。

## 文档更新触发条件

- 只有在以下情况才更新 `AGENTS.md`：
  - 本地长期工作方式发生变化；
  - 官方配置行为变更，且这会改变本地协作策略；
  - 现有内容已经明显过时，继续保留会误导执行。
- 若只是插件列表、模型名、agent 名称、category 默认值变化，优先改配置文件，不要同步扩写 `AGENTS.md`。

## 当前维护结论

- `AGENTS.md` 有保留价值，但应保持精简，定位为“稳定策略层”，而不是“配置镜像层”。
- 今后维护时优先检查：官方 docs / schema -> 本地 config -> `doctor` / 运行时输出 -> `AGENTS.md` 是否仍需补充。

