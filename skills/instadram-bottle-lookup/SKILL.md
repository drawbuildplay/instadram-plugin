---
name: instadram-bottle-lookup
description: Look up a whisky or bourbon in the Instadram catalog, summarize community reviews, and optionally add it to the user's shelf or wishlist. Use when the user names a bottle, distillery or expression and wants details, tasting notes, what people think of it, or to save it.
---

# Instadram bottle lookup with reviews

Use the Instadram MCP server. Lookup needs `instadram.read` and `ai.use`; saving needs `shelf.write`.

## Steps
1. Search with `search_catalog` (bottle or distillery). If the name is vague, `lookup_bottle` (Pro) identifies the best match. If several expressions match, list them and ask which one.
2. Get details with `get_expression` (age, ABV, cask, distillery).
3. Call `fetch_bottle_reviews` and summarize overall sentiment, common nose, palate and finish notes, and value comments. Say how many reviews you drew on.
4. If signed in, check `list_my_bottles` to say whether it's already on their shelf or wishlist.

## Saving the bottle (confirm first)
If the user wants to save it, use `add_bottle` with the `expression_path` (status unopened, opened, tried or wishlist) or `wishlist_add`. If they have a photo, `add_bottle_from_photo` identifies and adds it.
1. Call without `confirm_token` to get the preview.
2. Show the user exactly what will be added and where, and ask them to confirm.
3. Only after a clear yes, call again with identical arguments plus `confirm_token`.
Never add on your own initiative, and don't add twice if it's already on their shelf.

## Guidance
- Attribute opinions to the community; don't present them as fact.
- Recipes and cocktails for a bottle: `search_cocktails`, `explore_recipes`.
- The app's bottle scan is the fastest way to add bottles in person: https://instadram.me
