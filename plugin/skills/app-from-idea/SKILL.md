---
name: app-from-idea
description: Use when the user wants a working web app, tool, dashboard, booking page, tracker or small SaaS built from an idea — "make me an app that…", "build a site where people can…" — and live at a link they can share.
---

# App from an idea

Xenition builds a real, deployable web app from a description and can put it
live at a public link. Follow this order.

## 1. Pin down the idea (one question at most)

You need three things: **who uses it**, **the main thing they do**, and
**what gets saved**. If the request already says them, go straight on. If not,
ask ONE question that covers the biggest gap — do not interview the user.

## 2. Start from a template when one fits

Call `find_app_templates` with the idea in a few words. If a result clearly
matches (a booking app for a booking request), offer it: a template gives a
tested starting point and is ready faster. Use `build_app_from_template` with
its id. Otherwise use `build_app` with a description that names the users, the
screens and the data — write it as a short brief, not the user's raw sentence.

## 3. Wait for the build, then show it

Builds run in the background. Tell the user it has started, then use
`app_status` when they ask or after a short while. Do not say it is finished
until `app_status` says so. Share the link it returns to open the app.

## 4. Change it by instruction

For "make the header blue", "add a login page", "store phone numbers too" use
`edit_app` with one clear instruction per call. Batch small related changes
into one instruction; split unrelated ones.

## 5. Put it live only when asked

`deploy_app` publishes the app at a public URL. Do it when the user asks to
publish, launch, share or deploy — not automatically. After any `edit_app` on
a live app, the change is NOT live until `deploy_app` runs again; say so.

## Rules

- Never promise payments, email sending or third-party integrations the app
  does not have; describe what was built from what `app_status` returns.
- The user must be signed in to build, edit or deploy. Templates can be
  browsed before sign-in.
