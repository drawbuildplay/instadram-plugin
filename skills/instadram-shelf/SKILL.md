---
name: instadram-shelf
description: Browse and manage the user's Instadram whisky and bourbon shelf, collections and pour log. Use when the user asks what bottles they own, what's open, what they poured, or wants to add, edit, rate, move or remove a bottle, log a pour, organize collections, or look at another collector's public shelf.
---

# Instadram shelf, pours and collections

Use the Instadram MCP server. Reads need `instadram.read`; changes need `shelf.write` or `collections.write` (photo adds and art also need `ai.use`).

## Read
1. Call `whoami` to confirm the signed-in handle. If it fails, ask the user to connect Instadram (one-time OAuth sign-in, no keys).
2. Find bottles with `list_my_bottles` (filter by status or text). Page through all results before giving counts. Open one with `get_my_bottle`.
3. Use `list_my_collections` for collections and `list_my_activity` for pours, ratings and notes. `get_feed` shows the Home feed.
4. Someone else's public shelf: `search_users` or `get_user`, then `list_user_bottles`, `get_user_bottle`, `list_user_collections`, `list_user_activity`.

## Write (always confirm first)
Every write tool is two-step:
1. Call it **without** `confirm_token`. It returns a preview and a token; nothing has changed yet.
2. Show the user the preview in plain words (which bottle, what changes) and ask them to confirm.
3. Only after a clear yes, call again with **identical arguments** plus `confirm_token`. If they say no or change anything, don't commit; start a new preview if needed.

Never commit several changes on one vague "yes": list them and confirm the batch explicitly. Be extra clear for deletes (`remove_bottle`, `wishlist_remove`, `delete_collection`, `delete_my_activity`), which can't be undone, and for `log_pour` and `rate_bottle`, which post to followers' feeds.

Which tool:
- Add: `add_bottle` (use `search_catalog` first for an `expression_path`), or `add_bottle_from_photo` from a photo.
- Edit notes, price, store, batch, barrel, favorite: `update_bottle`. Rate 0-5 in 0.25 steps: `rate_bottle`.
- Open, finish or move: `set_bottle_status` (unopened, opened, finished, wishlist, tried).
- Wishlist: `wishlist_add`, `wishlist_remove`. Pour: `log_pour`. Delete a post: `delete_my_activity`. Delete a bottle: `remove_bottle`.
- New art or re-identify from the photo: `regenerate_art`, `reidentify_bottle`.
- Collections: `create_collection`, `rename_collection`, `delete_collection` (bottles stay on the shelf), `add_to_collection`, `remove_from_collection`.

## Guidance
- Only report what the tools return. Don't invent bottles, ratings or notes.
- If a write fails for a missing scope, tell the user which permission to grant and ask them to reconnect.
- The free plan holds 25 bottles on the shelf; if the commit hits that limit, say so and mention Pro in the app.
- Keep download pointers platform-neutral: https://instadram.me
