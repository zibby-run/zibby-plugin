# Zibby

Publish the web apps you build with your AI agent on [Zibby](https://zibby.run). This plugin connects your agent to your own Zibby account and teaches it the Zibby workflow: build the app on Zibby App Kit, make a private preview you can try, and publish it when you say so.

It works in Claude Code and in Codex. The same folder holds both formats.

## What your agent can do

- Read the Zibby App Kit guide and build the app on Zibby App Kit (`@zibby-run/app-kit`). Static apps and server (Node) apps are supported.
- Create the app on your account and send its source files, or connect a GitHub repository through an install link that you open yourself.
- Build a private preview and give you its link. Building a preview uses no credits.
- Publish the version you previewed, only when you ask. Publishing follows Zibby's app review: an app can go live at once or wait for review.
- Set the app's name, summary, description and category, and make an icon or a cover picture.
- Tell you your credit balance, how many free apps you have left, and where to top up.

Pictures, and publishing once your free apps are used up, use Zibby credits. You allow this spending once, on Zibby's consent page when you connect. After that the agent goes ahead when you ask for one of these actions and tells you what it used. When your balance is too low, it asks you to top up on [zibby.run/billing](https://zibby.run/billing). Credits are bought there, never in the chat.

You need a Zibby account with a confirmed email address. You sign in on Zibby's own sign-in page (OAuth); the plugin never sees your password.

## Install

### Claude Code

Once the plugin is listed, add it from the plugin directory: run `/plugin` in Claude Code, or open Customize, then Plugins, on claude.ai. Then run `/mcp`, choose `zibby` and sign in with your Zibby account.

To try a local copy of this folder before it is listed:

```bash
claude --plugin-dir ./zibby
```

### Codex

Once the plugin is listed, install it from the Plugins directory in Codex or the ChatGPT desktop app, and sign in with your Zibby account when asked.

To try a local copy, follow OpenAI's guide for a local marketplace: copy this folder to `~/.codex/plugins/zibby`, add an entry for it to `~/.agents/plugins/marketplace.json`, and restart the app.

### Any other MCP client

Add `https://zibby.run/mcp` as a remote (custom) connector and sign in with your Zibby account.

## What is inside

- `.claude-plugin/plugin.json`: the Claude Code manifest.
- `.codex-plugin/plugin.json`: the Codex manifest.
- `.mcp.json`: one remote MCP server, `zibby`, at `https://zibby.run/mcp`. It holds no keys or tokens.
- `skills/publish-on-zibby/SKILL.md`: how to build, preview and publish an app on Zibby, and how to handle credits.
- `skills/get-started/SKILL.md`: how to connect Zibby and show the account and its apps.
- `skills/check-before-publish/SKILL.md`: the check to run before every publish, so the app builds, works on a phone and passes Zibby's checks the first time.
- `skills/write-the-listing/SKILL.md`: how to write the app's name, summary, description and category so the right people find it.
- `skills/update-live-app/SKILL.md`: how to change a published app on a private preview without breaking it for the people using it.
- `assets/logo.svg`: the Zibby logo.

The plugin is Markdown and JSON only. It has no scripts and no hooks, and it runs nothing on your computer.

## Data

The plugin connects your agent to one server, `https://zibby.run/mcp`, over HTTPS. Through it the agent sends Zibby what you ask it to: your app's source files, the app's name and descriptions, and your requests to build, publish or make a picture. It reads back your account's credit balance and free apps, your apps, build logs and preview links. Zibby keeps your apps and account data as its privacy policy describes. The plugin itself stores nothing and sends nothing anywhere else.

- Privacy policy: https://zibby.run/legal/privacy
- Terms of use: https://zibby.run/legal/terms
- Support: https://zibby.run/support

## License

MIT, published by Aibrary LTD. See `LICENSE`.
