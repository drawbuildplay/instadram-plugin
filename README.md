<p align="center"><img src="assets/logo.png" width="96" alt="Instadram"></p>

# Instadram plugin

Your whisky & bourbon collection in any AI: catalog search, your shelf, public shelves.

[Instadram](https://instadram.me) is a whisky and bourbon collection app with bottle scan. This plugin connects Grok, Cursor and other agents to the hosted Instadram MCP server so they can read your collection, search the public bottle catalog, check community reviews, and browse other collectors' public shelves. **It is read-only:** it never adds, edits or deletes bottles.

## What's included
- **MCP server:** `https://api.instadram.me/mcp` (remote, Streamable HTTP). Sign in once with your Instadram account via OAuth 2.1 (PKCE, dynamic client registration). No API keys. Scope: `instadram.read`.
- **Skills:**
  - `instadram-shelf`: browse and search your shelf, collections and pour log, or a public collector's shelf.
  - `instadram-bottle-lookup`: find a bottle in the catalog and summarize community reviews.

## Example prompts
1. What unopened bottles do I have, sorted by distillery?
2. Look up Blanton's Original Single Barrel and summarize community reviews.
3. Show me @amit's public shelf and what he poured last.
4. Which of my collections has the most ryes?

## Tools (15, all read-only)
`whoami`, `search_catalog`, `lookup_bottle`, `get_expression`, `fetch_bottle_reviews`, `list_my_bottles`, `get_my_bottle`, `list_my_collections`, `list_my_activity`, `search_users`, `get_user`, `list_user_bottles`, `get_user_bottle`, `list_user_collections`, `list_user_activity`.

No email or billing data is ever returned.

## Manual setup
```json
{ "mcpServers": { "instadram": { "url": "https://api.instadram.me/mcp" } } }
```

## Get Instadram
Get the app at https://instadram.me · Support: https://instadram.me/support

## License
The plugin files in this repo (manifest, skills, README) are MIT licensed. The Instadram service is proprietary and hosted by DrawBuildPlay LLC.
