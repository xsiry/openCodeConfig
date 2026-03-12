# OpenCode 本地 AGENTS 约定

## 作用

- 本文件只保留当前用户长期有效的全局协作约束；OpenCode / Oh-My-OpenCode 的运行时配置以 `~/.config/opencode/opencode.jsonc` 和 `~/.config/opencode/oh-my-opencode.jsonc` 为准，不在此重复 agent、category、skill、model、MCP、plugin、hook 等动态事实。
- 若本文件与运行时工具、官方文档或 `doctor` 输出冲突，以实际运行结果为准；凡是可以稳定写入配置文件或 schema 的内容，都不要写进本文件。

## 长期约束

- Thinking 使用中文；面向用户的回复默认使用简体中文，除非用户明确要求其他语言；文件统一使用 UTF-8，除非文件本身已使用其他字符集，否则不要引入 GBK / ANSI。
- 优先使用官方来源；非官方镜像、第三方搬运站或付费分发站点不能作为规范依据。
- 优先复用仓库现有实现、命名、结构和约定；以最小安全改动完成任务，不为了“更优雅”主动偏离项目风格。在引入新的第三方依赖或框架前，必须先检查项目的依赖配置文件（如 `package.json` 等），若需新增依赖必须先征得用户同意。
- 结论优先基于实际读取、搜索、诊断或验证结果，不对未读代码和未验证行为作判断。遇到报错或执行异常时，严禁“盲猜”修复，必须基于真实的错误日志和局部代码读取进行分析闭环。
- 结构化代码分析优先 `serena`，其次 `lsp_*`，最后才是纯文本搜索；小范围精确修改优先 `apply_patch`，大文件或分散改动优先 `morph_edit`。工具失败时，平滑降级至基础搜索与替换工具。
- 阅读代码秉持“按需加载”原则，避免无意义的全文件读取；利用搜索和符号树精确锁定上下文范围。
- 除非用户明确指令，严禁主动执行破坏性命令（如 `rm -rf` 等不可逆操作）或直接进行 Git 提交。若需提交，必须先检查变更并提供 Commit Message 草稿供确认。
- 验证 OpenCode 配置时优先查看官方 config docs / schema 与本地 `opencode.jsonc`；验证 Oh-My-OpenCode 配置时优先查看官方 GitHub Repo / Release / schema 与本地 `oh-my-opencode.jsonc`，必要时运行 `bunx oh-my-opencode doctor --json` 或 `--verbose`。

## 维护

- 仅在本地长期工作方式变化，或官方行为变更已影响本地协作策略时更新本文件。
- 若只是模型、agent、插件、category、hook 等配置变化，优先修改 JSONC 配置，不同步扩写本文件。