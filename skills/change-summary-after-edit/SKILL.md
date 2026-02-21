---
name: change-summary-after-edit
description: Use when user asks to modify documents/content/code and wants a mandatory post-edit summary explaining before/after changes and the practical meaning of each change.
---

# Change Summary After Edit

## When To Use
Use this skill when:
- The user asks for any content or code modification.
- The user requests a change report, revision summary, or "修改总结".
- The task includes committing or pushing changes after edits.

Do not use this skill for pure Q&A without file edits.

## Required Workflow
1. Complete the requested edits first.
2. Compare edited files against previous state (`git diff` or equivalent).
3. Produce a mandatory summary in the final response.
4. Append the same summary to root document `版本更新内容.md`.
5. If `版本更新内容.md` does not exist, create it first in repository root.
6. If the user requested GitHub submission, commit with a clear message and push.

## Required Summary Format
Use exactly these sections after every edit task:

### 1) 修改文件
- List changed files.

### 2) 修改前 -> 修改后
- For each file, describe key differences in plain language.
- Focus on structure, rules, logic, data fields, and constraints.

### 3) 修改意义
- Explain why changes matter (compliance, readability, maintainability, execution efficiency, risk reduction, etc.).

### 4) 提交信息（如已提交）
- Commit hash and message.
- Remote branch and push status.

## Root Version Log Requirement
- File path: `./版本更新内容.md`
- After every edit task, append one new entry.
- Entry must include:
  - Date/time
  - 修改文件
  - 修改前 -> 修改后
  - 修改意义
  - 提交信息（如有）
- Newest entry should be added at top for quick review.

## Quality Bar
- No vague lines like “优化了一下” without concrete detail.
- Each meaningful change must have both “what changed” and “why it matters”.
- Keep summary concise but complete.
