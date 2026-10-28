# MY EPK for Claude

Build an electronic press kit (EPK) for a DJ, producer, singer, rapper or band without leaving the chat.
Claude drafts the kit, finds the artist's streaming profiles, imports releases with artwork, writes a short
bio, and hands the artist one link to add photos, sign in and publish at `my-epk.com/<handle>`.

## Install

In Claude Code:

    /plugin install my-epk --marketplace skelly1313/my-epk-claude-plugin

Then ask: "I'm a house DJ from Brooklyn, make me an EPK."

## What is inside

| Path | What |
|---|---|
| `.mcp.json` | The MY EPK server at https://my-epk.com/mcp (HTTP, no sign in needed) |
| `skills/make-an-epk/` | When to build a kit and the six step flow |
| `evals/` | Test cases for `claude plugin eval`; `evals/mocks/` answers every tool, so a test run never creates a real kit |

## How it works

The server's tools: `create_kit`, `get_kit`, `update_kit`, `find_profiles`, `resolve_link`, `import_catalog`,
`add_photos`, `set_handle` and `publish_kit`. A kit is a private draft until the artist opens their claim link,
adds photos, signs in and taps Publish. Claude cannot publish for them.

## Test it

    claude plugin eval . --ablation with-without

## Support

shawn@my-epk.com · https://my-epk.com/support · Privacy: https://my-epk.com/privacy

MIT licensed.
