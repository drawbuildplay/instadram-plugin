<p align="center"><img src="assets/logo.png" width="96" alt="Instadram"></p>

# Instadram plugin

Your whisky & bourbon collection in any AI: catalog, reviews, your shelf, pours, collections and public shelves.

[Instadram](https://instadram.me) is a whisky and bourbon collection app with bottle scan. This plugin connects Grok, Cursor and other agents to the hosted Instadram MCP server. Agents can read your collection, search the bottle catalog, summarize community reviews and browse other collectors' public shelves. With your permission they can also manage your shelf: add bottles (by name or photo), edit, rate and move them, log pours, organize collections, follow collectors and update your profile.

**Every write is two-step.** The first call returns a preview and a `confirm_token`. Nothing changes until the agent calls again with the same arguments and the token, which it should only do after you say yes. You choose which permissions to grant when you sign in.

## What's included
- **MCP server:** `https://api.instadram.me/mcp` (remote, Streamable HTTP). Sign in once with your Instadram account via OAuth 2.1 (PKCE, dynamic client registration). No API keys.
- **Skills:**
  - `instadram-shelf`: browse your shelf, collections and pours, and add, edit, rate, move or remove bottles, log pours and manage collections after you confirm.
  - `instadram-bottle-lookup`: find a bottle, summarize community reviews, and optionally add it to your shelf or wishlist after you confirm.

## OAuth scopes
| Scope | Grants |
|---|---|
| `instadram.read` | Read your shelf, pours, collections, feed, public profiles and the catalog |
| `ai.use` | AI features: bottle lookup, community reviews, cocktail/recipe search, photo identification and bottle art |
| `shelf.write` | Add, edit, rate, move and remove bottles; wishlist; log and delete pours |
| `collections.write` | Create, rename and delete collections; add or remove bottles |
| `social.write` | Follow, unfollow, block, unblock all |
| `profile.write` | Edit profile, change handle, send feedback |

## Tools (46)
**Read (`instadram.read`):** `whoami`, `list_my_bottles`, `get_my_bottle`, `list_my_collections`, `list_my_activity`, `search_catalog`, `get_expression`, `search_users`, `get_user`, `list_user_bottles`, `get_user_bottle`, `list_user_collections`, `list_user_activity`, `get_feed`, `explore_catalog`, `discover_users`, `check_username`, `export_shelf` (Pro).

**AI (`ai.use`):** `lookup_bottle` (Pro), `fetch_bottle_reviews`, `search_cocktails`, `explore_recipes`.

**Shelf (`shelf.write`):** `add_bottle`, `update_bottle`, `set_bottle_status`, `rate_bottle`, `remove_bottle`, `wishlist_add`, `wishlist_remove`, `log_pour`, `delete_my_activity`.

**AI + shelf (`ai.use` + `shelf.write`):** `add_bottle_from_photo`, `regenerate_art`, `reidentify_bottle`.

**Collections (`collections.write`):** `create_collection`, `rename_collection`, `delete_collection`, `add_to_collection`, `remove_from_collection`.

**Social (`social.write`):** `follow_user`, `unfollow_user`, `block_user`, `unblock_all_users`.

**Profile (`profile.write`):** `update_profile`, `set_username`, `send_feedback`.

Free and Pro limits match the app (for example the free 25-bottle shelf limit). Your user id always comes from your sign-in, so tools can only change your own data. No email or billing data is ever returned.

## Example prompts
1. What unopened bottles do I have, sorted by distillery?
2. Look up Blanton's Original Single Barrel, summarize the reviews, and add it to my wishlist.
3. I just opened my Eagle Rare. Mark it opened and log a pour.
4. Make a "Ryes" collection and put all my ryes in it.
5. Show me @amit's public shelf and follow him.

## Manual setup
```json
{ "mcpServers": { "instadram": { "url": "https://api.instadram.me/mcp" } } }
```

## Get Instadram
Get the app at https://instadram.me · Support: https://instadram.me/support

## License
The plugin files in this repo (manifest, skills, README) are MIT licensed. The Instadram service is proprietary and hosted by DrawBuildPlay LLC.
