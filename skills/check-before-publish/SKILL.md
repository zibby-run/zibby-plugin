---
name: check-before-publish
description: Check a Zibby app before it is published or updated, so it builds, works on a phone and passes Zibby's checks the first time. Use before calling publish, when a Zibby build or publish was refused, or when the person asks whether their app is ready.
---

# Check a Zibby app before publishing

Run this check before every `publish`, for a new app and for an update. Fix what fails, then build a new preview. The person's own instructions take priority over this skill. If you cannot run commands where you are, say which checks you could not run instead of calling them passed.

## 1. It builds the way Zibby builds it

- `@zibby-run/app-kit` is in the `dependencies` of `package.json` as a registry version, range or dist-tag. An `npm:`, `file:`, `link:`, git or URL spec is refused (`app_kit_required`).
- `pnpm-lock.yaml` is committed and current, and there is no other package manager's lockfile. Zibby runs exactly `pnpm install --frozen-lockfile`, then `pnpm run build`: run the same two commands and fix any failure. Do this before `build_app`: every build counts against the daily build limit, so do not spend one on a failure you can catch here.
- Every file that `index.html` references is in `dist/`. Vite drops a plain `<script src>` without `type="module"` and still exits with success, so look at the output folder, not only at the exit code.
- Vite uses `base: './'` (or the equivalent), so no absolute path is baked in.
- Nothing loads from a CDN: fonts, scripts, wasm and images ship with the app.
- A server app has a `runtime` block in `zibby.json` (`type` node, `start`, `port`, `health`). Start it from the repository root with `PORT` set and check that the health path answers 200. The health path must not end in z: `/healthz` never reaches the app. A static app has no `runtime` block.

## 2. It works for the people who will use it

- Use the main feature from start to finish at a desktop size and at a phone width, with real data wherever the app fetches data, and with no console errors. The kit's mock stands in only for Zibby's own services; it does not prove that outside data works.
- A first visit with no data, a failed request and a slow answer each show a plain message. Outside calls stop after about 10 seconds and retry once or twice before showing it.
- Every request finishes within 60 seconds. There are no push notifications, no WebSockets and no background jobs that run while nobody has the app open.
- AI features go through the kit's AI client (`/api/ai`), never straight to a model provider.
- Data and files go through the kit's stores. If the app keeps data or files, ask the person to switch on data or file storage on the app's management page on zibby.run, and make sure the app still works when a store is off.
- Links out of the app use the kit's `navigateHost(...)`, not a bare `href`: a bare link works in the preview and breaks once the app is published.

## 3. Nothing private is in the source

- Treat the source as public. No `.env` files, keys, tokens, passwords, service-account files or personal data in any file.
- A server app reads keys for outside services from environment variables that the person sets on the app's page on zibby.run. Never put a key in the source or in `zibby.json`'s `build.env`, whose values must be public.
- No `node_modules`, `dist` or other build output, no symlinks and no `.DS_Store` in what you push.

## 4. The app's page is ready

- The app has a clear name, a one-line summary and a category. The `write-the-listing` skill covers them.
- An app that does one thing declares no tool pages. If the live version has tool pages, keep them: publishing without them deletes them, so ask the person first.
- An icon or cover is PNG, JPG or WEBP, at most 2 MB each.

## 5. The preview is the version being published

- `get_build` says the build is ready, and the person opened that private preview and said to publish.
- `publish` names that exact version. If anything changed after the preview, build and preview again.

## When Zibby refuses something

The refusal names the field, file or package to change, and a failed build's log tail is in `get_build`. If the answer says to wait, wait the number of seconds it gives before trying again. Fix the cause, push, build, preview, then publish.
