---
name: update-live-app
description: Change an app that is already published on Zibby without breaking it for the people who use it. Use when the person asks to fix, change or add to a Zibby app that is live or waiting for review.
---

# Update a live app on Zibby

The published version stays live until the person publishes a new one. Work on a private preview, and switch only when they say so. The person's own instructions take priority over this skill.

1. Find the app with `list_my_apps` and confirm with the person which app to change.
2. Work from the app's current source: the person's local folder, or the GitHub repository the app is connected to. If neither is at hand, ask where the source is. Do not rebuild the app from memory.
3. Keep the change to what the person asked for, and tell them what will change for the people using the app.
4. If the app keeps data with the kit's data store, the new version must still read everything earlier versions saved. When the shape of saved data changes, read the old shape and convert it; never drop or overwrite it. Try the new version with data that the live version saved.
5. Keep every tool page the live version declares unless the person asks to remove one. Publishing without them deletes them.
6. Send the change. For an app updated through Zibby, use `push_files`. For an app connected to GitHub, the change goes into its repository the way the person usually works, and Zibby builds it from there.
7. Run the `check-before-publish` skill's local checks, then build a new private preview (`build_app`, then `get_build` or `list_builds`). Every build counts against the daily build limit. Give the person the preview link with a short list of what changed. The live version is still unchanged.
8. Publish only when the person says so, naming the version they previewed. Zibby's app review can hold a new version for review; the live version stays live until it is approved. Tell the person which happened. If `publish` answers that the balance is too low, follow the credit rule in the `publish-on-zibby` skill.
9. If the person drops the change before publishing, nothing needs undoing: the live version was never touched.

A new name, summary, description or category needs no new version: use the `write-the-listing` skill.
