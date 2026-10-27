---
name: get-started
description: Connect Zibby and show what it can do. Use when the person has just added the Zibby plugin, asks how to start with Zibby, or asks to connect or sign in to Zibby.
---

# Get started with Zibby

The person's own instructions always take priority over this skill.

1. Call `my_account`. If the Zibby tools are missing, or the answer says the person is not signed in, the Zibby server is not connected yet. Ask them to connect it in their app's connector or MCP settings and sign in with their Zibby account. Anyone with a confirmed Zibby account can connect; a new account is made on https://zibby.run. Then call `my_account` again.
2. Tell the person in two or three short lines which account is connected, their credit balance, how many free apps they have left and how many builds they have left today. Do not paste the raw answer.
3. Call `list_my_apps` and name their apps, if they have any, with each app's status.
4. Offer the next step in one sentence: build a new app on Zibby App Kit and publish it, or update one of their apps. For a new app, follow the `publish-on-zibby` skill; for a published one, the `update-live-app` skill.
