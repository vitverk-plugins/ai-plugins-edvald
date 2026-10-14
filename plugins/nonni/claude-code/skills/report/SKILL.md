---
name: report
description: Answer a question about Nonni's company data with a sourced, read-only report.
argument-hint: "<question>"
context: fork
agent: nonni:analyst
disable-model-invocation: true
---

# Report for Nonni

Answer this from Nonni's data, read-only: $ARGUMENTS

If the nonni:analyst subagent is unavailable, follow this plugin's own workflow skill directly.
