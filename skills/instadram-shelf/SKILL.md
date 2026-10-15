---
name: instadram-shelf
description: Browse and search the user's Instadram whisky and bourbon shelf, collections and pour log. Use when the user asks what bottles they own, what's open or unopened, what they poured recently, or what's on another collector's public shelf.
---

# Instadram shelf and pour log

Use the Instadram MCP server (read-only, scope `instadram.read`). It never adds, edits or deletes bottles.

## Steps
1. Call `whoami` to confirm the signed-in handle. If it fails, ask the user to connect Instadram (one-time OAuth sign-in, no keys).
2. Find bottles with `list_my_bottles` (filter by status such as open/unopened, or by text such as a distillery). Page through all results before summarizing counts.
3. Open one bottle with `get_my_bottle`. Use `list_my_collections` for shelf groups and `list_my_activity` for pours and tasting notes.
4. For someone else's public shelf: `search_users` or `get_user`, then `list_user_bottles`, `list_user_collections`, `list_user_activity`, `get_user_bottle`.

## Guidance
- Only report what the tools return. Don't invent bottles, ratings or notes.
- To add a bottle or log a pour, point the user to the Instadram app (bottle scan makes adding fast). This connector can't write.
- Keep download pointers platform-neutral: https://instadram.me
