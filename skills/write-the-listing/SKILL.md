---
name: write-the-listing
description: Write a Zibby app's name, one-line summary, description and category so the right people find it and open it. Use when the person publishes a new app on Zibby, asks to improve how their app looks on Zibby, or wants a better name or description.
---

# Write the app's listing on Zibby

The listing is what people see in Zibby's catalogue and on the app's page: the name, a one-line summary, the description, the category, and the icon and cover. Write it for the people who will use the app. The person's own words and choices always win: suggest text, show it, and set it only when they agree.

## Before writing

Find out, from the person or from the app itself: who the app is for, the one job it does, and the words someone would type to look for it.

## Name

- Short and plain: what the app does, or a memorable word next to what it does, such as "Tip Splitter".
- No version numbers and no capitals for emphasis. Add "AI" only when it tells people something they need.

## Summary

- Cards show the summary on a single line and cut it off with "…" when it is too long. Keep it under about 60 characters and put the words people search for first.
- Say what the person gets: "Split a restaurant bill and tip in seconds", not "An app that helps you with bills".

## Description (`about`)

- The page shows it as plain paragraphs separated by blank lines. Headings, lists and links show as plain text, so write sentences.
- First paragraph: what the app does and who it is for, in two or three sentences.
- Then how to use it in a sentence or two, what it keeps (say so if it saves data or files), and whether it uses AI credits.
- Claim only what the app does. No invented numbers of users, ratings or awards.

## Category

- Use a category that already exists on Zibby, spelled exactly the same, for example Photos, Utilities, Marketing or E-commerce. The catalogue groups apps by the exact name, so a new spelling starts a group of one.

## Tool pages

- An app with several distinct tools can have a page for each. Pages are declared in the app's source, as the App Kit reference from `get_app_guide` describes, not with `set_details`. Write each page's title (3 to 80 characters) and description (50 to 300 characters) the same way: what that tool does, for whom, in plain words.

## Icon and cover

- Icon: one simple shape or symbol that reads at a small size, with no text in it.
- Cover: the app in use, or what it produces.
- Every picture uses credits, so make one only when the person asks for it. The `publish-on-zibby` skill covers how credits are spent and what to do when the balance is too low.

## Set it

1. Show the person the name, summary, description and category together, and change what they ask for.
2. Call `set_details` with exactly the agreed text. It does not publish a new version.
3. `set_details` also takes a `slug`, which changes the app's address. Send one only when the person asks for a new address, and tell them the old address changes.
4. To change the text later, call `set_details` again.
