# SKILLS DEVELOPMENT GUIDE

**Scope**: Custom skills in `skills/` directory.

## OVERVIEW
本目录包含自定义 OpenCode 技能。每个子目录代表一个独立的技能单元。

## STRUCTURE
```
skills/
├── {skill_name}/
│   ├── SKILL.md      # 技能文档 (Required)
│   ├── scripts/      # 实现脚本 (Python/Node)
│   ├── data/         # 静态资源
│   └── LICENSE.txt   # 许可证
```

## CONVENTIONS
1. **Self-Contained**: 技能应自包含，避免跨技能依赖。
2. **Documentation**: 必须包含 `SKILL.md`，描述技能用途、参数与示例。
3. **Scripts**: 推荐使用 Python 处理数据，Node.js 处理 IO/Web。
4. **Resources**: 静态文件（模板、数据）应放在 `data/` 子目录。
