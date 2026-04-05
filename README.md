# openclaw-clickup-native-integration

[![Release](https://img.shields.io/github/v/release/muhamadbasim/openclaw-clickup-native-integration)](https://github.com/muhamadbasim/openclaw-clickup-native-integration/releases)
[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](LICENSE)
[![Companion Guide](https://img.shields.io/badge/companion-MCP%20route-blue)](https://github.com/muhamadbasim/integration-to-clickup-with-mcp)

A practical guide for using **native ClickUp tools already exposed by OpenClaw**, without going through MCP.

This repository exists as a lightweight reference so you can come back later, read the tutorial, and immediately understand the working path.

## Table of contents

- [What this repository covers](#what-this-repository-covers)
- [When to use this route](#when-to-use-this-route)
- [When to use the MCP route instead](#when-to-use-the-mcp-route-instead)
- [What was tested successfully](#what-was-tested-successfully)
- [Quick comparison](#quick-comparison)
- [Example workflow](#example-workflow)
- [Recommended operating pattern](#recommended-operating-pattern)
- [Pros and cons](#pros-and-cons)
- [How to verify in your own environment](#how-to-verify-in-your-own-environment)
- [Release download](#release-download)

## What this repository covers

This guide is about the **native OpenClaw ClickUp toolset** — tools with names like:

- `clickup__get_workspaces`
- `clickup__get_spaces`
- `clickup__get_tasks`
- `clickup__create_task`
- `clickup__update_task`
- `clickup__create_task_comment`
- `clickup__create_checklist`
- `clickup__create_checklist_item`

If your OpenClaw runtime already exposes these tools, you can work with ClickUp directly from the assistant without setting up MCP.

## When to use this route

Use this route when:

- your OpenClaw environment already has built-in ClickUp tools
- you want the simplest path
- you do not want to maintain manual MCP config
- you just need working task operations now

## When to use the MCP route instead

Use the MCP route when you specifically want:

- a reusable manual MCP definition in OpenClaw config
- a separate integration path based on `clickup-mcp-server`
- an installable MCP setup you can reapply later

See companion repo:

- <https://github.com/muhamadbasim/integration-to-clickup-with-mcp>

## What was tested successfully

In the tested OpenClaw environment, these operations worked:

- list ClickUp workspaces
- list spaces
- list lists
- create a task
- add a task comment
- create a checklist
- create checklist items

## Quick comparison

| Topic | Native route | MCP route |
| --- | --- | --- |
| Setup complexity | Lower | Medium |
| Best for | Immediate use | Reusable setup |
| Extra config needed | Usually no | Yes |
| Portability | Lower | Higher |
| Companion repo | This repo | `integration-to-clickup-with-mcp` |

## Example workflow

### 1) Check available workspaces

Expected operation:
- call `clickup__get_workspaces`

Example output:

```json
[
  {
    "id": "90182591141",
    "name": "Basim's Workspace"
  }
]
```

### 2) Check spaces in the workspace

Expected operation:
- call `clickup__get_spaces` with the workspace ID

Example output:

```json
[
  {
    "id": "901810490603",
    "name": "Team Space"
  }
]
```

### 3) Choose a list and create a task

One tested list:

```text
List ID: 901817158899
List name: Project 1
```

Example task creation result:

```json
{
  "id": "86ex543cr",
  "name": "TEST - Contoh task dari OpenClaw",
  "status": { "status": "to do" },
  "url": "https://app.clickup.com/t/86ex543cr"
}
```

### 4) Add a comment

Example comment content:

```text
Komentar test dari OpenClaw: integrasi create comment berhasil dicek.
```

### 5) Add a checklist

Example checklist:

```text
Checklist testing OpenClaw
```

Example checklist items:

```text
✅ Cek create task
✅ Cek comment task
⬜ Cek checklist item
```

## Recommended operating pattern

If you already have native ClickUp tools, the safest practical workflow is:

1. get workspace
2. get spaces
3. get lists
4. create a clearly-labeled test task
5. add comment/checklist only after task creation succeeds
6. clean up test data if no longer needed

## Pros and cons

### Pros

- no MCP setup needed
- fewer moving parts
- simpler day-to-day usage
- direct OpenClaw tool access

### Cons

- depends on your OpenClaw environment already exposing ClickUp tools
- not as portable as a documented MCP config
- another machine/session may not have the same built-in tool availability

## How to verify in your own environment

Try these in order from your OpenClaw session:

1. list workspaces
2. list spaces
3. inspect available lists
4. create a test task
5. add a comment or checklist

If step 1 already fails because the ClickUp tools are unavailable, then use the MCP guide instead:

- <https://github.com/muhamadbasim/integration-to-clickup-with-mcp>

## Release download

- Releases page: <https://github.com/muhamadbasim/openclaw-clickup-native-integration/releases>
- Latest ZIP release: <https://github.com/muhamadbasim/openclaw-clickup-native-integration/releases/latest>

## Notes

This repository intentionally documents the **native route only**.

It does not try to force installation because native ClickUp support depends on the OpenClaw runtime/environment that is already running.

## License

MIT
