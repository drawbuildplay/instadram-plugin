---
name: instadram-bottle-lookup
description: Look up a whisky or bourbon in the Instadram catalog and summarize community reviews. Use when the user names a bottle, distillery or expression and wants details, tasting notes or what people think of it.
---

# Instadram bottle lookup with reviews

Use the Instadram MCP server (read-only).

## Steps
1. Search the catalog with `search_catalog` (bottle or distillery name). If the name is vague, use `lookup_bottle` to identify the best match.
2. Get details with `get_expression` (age, ABV, cask, distillery).
3. Call `fetch_bottle_reviews` and summarize overall sentiment, common tasting notes (nose, palate, finish) and value comments. Say how many reviews you drew on.
4. If signed in, optionally check `list_my_bottles` to tell the user whether it's already on their shelf.

## Guidance
- Attribute opinions to the community; don't present them as fact.
- If several expressions match, list them and ask which one.
- To add the bottle, suggest bottle scan in the Instadram app: https://instadram.me
