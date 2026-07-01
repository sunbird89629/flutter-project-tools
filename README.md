# flutter-project-tools

> Claude Code skill for analyzing Flutter/Dart projects — run diagnostics, collect logs, diagnose issues, and generate error reports **without modifying source code**.

**Language**: [English](README.md) · [简体中文](#简体中文)

---

## What is this

A specialized [Claude Code skill](https://docs.claude.com/en/docs/claude-code) that turns Claude into an *observer* of your Flutter project. It runs the standard diagnostic commands, captures their output, and synthesizes a detailed error report — but it never touches your source.

Useful when:
- You want an objective "what's broken here?" report before you start fixing
- CI is failing and you want a summary before diving in
- You're onboarding to an unfamiliar Flutter codebase

## Installation

Symlink or copy `SKILL.md` into one of your Claude Code skill directories:

```bash
# global
ln -s $(pwd)/SKILL.md ~/.claude/skills/flutter-project-tools/SKILL.md

# per-project
mkdir -p .claude/skills/flutter-project-tools
ln -s $(pwd)/SKILL.md .claude/skills/flutter-project-tools/SKILL.md
```

Then in Claude Code, ask:

> Run project and report errors
> Analyze build failures
> Diagnose project issues

Claude will invoke this skill automatically.

## What it does

1. **Project inspection** — read `pubspec.yaml`, find entry points
2. **Static analysis** — `dart analyze` / `flutter analyze`
3. **Dependency check** — `flutter pub get`
4. **Build verification** — `flutter build bundle`
5. **Report synthesis** — structured error report with root-cause hints

Uses `build` commands over `run` to avoid interactive session hangs.

## Non-goals

- ❌ Does NOT modify source code
- ❌ Does NOT attempt automatic fixes
- ✅ Observation and diagnosis only

## License

MIT

---

## 简体中文

一个 [Claude Code skill](https://docs.claude.com/en/docs/claude-code)，让 Claude 变成 Flutter 项目的**旁观诊断者** —— 跑诊断命令、抓日志、出错误报告，但**不动源码**。

适用场景：
- 想要在动手前先看一份客观的"哪里坏了"报告
- CI 挂了想快速总结
- 接手陌生 Flutter 代码库时

安装方式和使用方法见上文英文版。
