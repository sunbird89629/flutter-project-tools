---
name: flutter-project-tools
description: Specialized workflow for analyzing Flutter/Dart projects, collecting execution/build logs, diagnosing issues, and generating detailed error reports without modifying source code. Use when the user asks to "run project and report errors", "analyze build failures", or "diagnose project issues".
---

# Flutter Project Tools

## Overview

This skill enables the autonomous analysis of Flutter projects by running diagnostic commands, capturing output, and synthesizing findings into a comprehensive error report. It focuses on observation and diagnosis rather than automatic remediation.

## Workflow

### 1. Project Inspection
Before running diagnostics, understand the project context:
- Read `pubspec.yaml` to identify dependencies and SDK constraints.
- Check `lib/main.dart` or `test/` directory to understand entry points.

### 2. Diagnostic Execution
Run the following commands in order to gather information. capture `stdout` and `stderr` for analysis.

**A. Static Analysis**
Run `dart analyze` or `flutter analyze` to identify compile-time errors, type mismatches, and linter warnings.

**B. Dependency Check**
Run `flutter pub get` to ensure dependencies are resolved. If this fails, report the version conflicts.

**C. Build Verification**
Run `flutter build bundle` (or a specific target like `apk`/`ios` if requested) to verify the build process.
*Note: Prefer `build` commands over `flutter run` for automated diagnosis to avoid interactive session hangs.*

**D. Test Execution (Optional)**
If tests exist and the user implies runtime checking, run `flutter test`.

### 3. Log Analysis
Examine the captured output for:
- **Keywords**: "Error", "Exception", "Failed", "Compiler message", "undefined".
- **Locations**: File paths and line numbers associated with errors.
- **Patterns**: Stack traces pointing to specific packages or custom code.

### 4. Error Report Generation
Create a Markdown report summarizing the findings. Do **not** modify the code.

#### Report Template

```markdown
# Diagnostic Report: [Project Name]

## Summary
**Status**: [Build Passed / Build Failed / Analysis Issues]
**Date**: [YYYY-MM-DD]

## Critical Errors
- **Error**: [Brief description of error]
  - **Location**: `[File Path]:[Line Number]`
  - **Context**: [Code snippet or log extract]
  - **Analysis**: [Explanation of what caused the error]

## Warnings & Recommendations
- [List of warnings or less critical issues]
- [Suggested next steps for the user]

## Raw Logs (Snippet)
```text
[Paste relevant log segments here]
```
```

## Constraints
- **Read-Only**: Do not apply fixes automatically.
- **Safety**: Ensure commands do not inadvertently modify state beyond build artifacts.