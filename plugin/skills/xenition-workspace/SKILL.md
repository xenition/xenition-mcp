---
name: xenition-workspace
description: Use when the user wants to work with their Xenition workspace — create or edit content, ask about or search their own files, run their agents, build and deploy an app, schedule an automation, make images, videos and voiceovers, generate 3D models, build and share forms and read their responses — or get an answer from one of Xenition's built-in calculators and converters.
---

# Xenition

Xenition is the signed-in user's content workspace (documents, slides,
spreadsheets, notes, boards, media, 3D models, forms, and AI agents). Use its
tools whenever the user refers to "my Xenition …", to their own files/notes/
data, or asks to make something (a deck, doc, sheet, 3D model, form) or run
their agents. Do not use these tools for general knowledge questions.

## When to use which tool

- **Find / read the user's own content:** `search_artifacts` and
  `get_artifact` to locate and open items; `ask_workspace` for a grounded answer
  across their files (with sources); `query_document` to answer a question about
  one specific document; `summarize_artifact` for a TL;DR, key points, or action
  items; `extract_from_artifact` to pull a specific thing (dates, names, totals)
  as a list; `query_spreadsheet` to compute or answer over a sheet.

- **Create content:** `create_slides` (a designed deck), `create_3d_model`
  (text/image → 3D), and the document / spreadsheet / diagram / board creators.
  Use `repurpose_artifact` to turn one artifact into another surface (e.g.
  meeting notes → a task board, a document → a slide deck).

- **Edit or review existing content:** `edit_artifact` to change an item in
  place (rewrite, shorten, translate, fix); `review_artifact` to return
  constructive comments tied to quoted passages **without** changing the file.

- **Built-in tools (no sign-in needed):** `find_tools` to find a calculator,
  converter or generator by what the user wants, then `run_tool` with its id to
  compute the answer in the chat — unit conversions, loan payments, BMI, tip
  splits, discounts, sales tax, percentages, temperature, age. Interactive tools
  (timers, QR codes, live weather) come back with a link that opens them ready to
  use; say so rather than inventing a result.

- **Forms:** `find_forms` then `submit_form` to fill a built-in template into a
  finished document; `create_shared_form` to make a fillable form with a public
  link that collects responses in Xenition.

- **Apps:** `build_app` makes a working web app from a description (or
  `find_app_templates` then `build_app_from_template` for a ready-made starting
  point); `app_status` shows build/deploy progress; `edit_app` changes it by
  instruction; `deploy_app` puts it live. After `edit_app` on a live app, call
  `deploy_app` again — edits do not go live on their own.

- **Automations:** `create_automation` runs a goal on a schedule (daily at a
  time, weekly on days, or every N hours — 15 minutes minimum);
  `list_automations` and `set_automation_enabled` to review, pause or resume.
  Confirm the schedule and time zone with the user before creating one.

- **Files in and out:** `transcribe_audio` turns a public https recording link
  into a saved transcript; `export_pdf` returns a document as a PDF download
  link; `form_responses` reads what people submitted to a shared form;
  `search_marketplace` finds public listings.

- **Remember material:** `add_to_knowledge` saves pasted notes or a public web
  page privately to the user's knowledge; `ask_workspace` then answers from it
  with sources. Text and web pages only (PDF and Word files are uploaded in
  Xenition).

- **Media:** `create_image` and `edit_image` (edit, upscale, remove
  background…); `create_video` then `video_status` — a clip takes a few
  minutes, so start it, say so, and check when asked; `edit_video` adds
  captions, cleans up picture and sound, removes the background or cuts
  silences; `create_speech` reads text aloud. Everything lands in the user's
  library with a link.

- **Agents & research:** `list_agents` to see the user's AI agents, then
  `run_agent` to start one on a task; `check_agent_run` (or `get_mission`) to
  fetch status and the final result of a background run.

- **Workspace actions:** board, calendar, notes, sheet, and ledger tools to
  read and update those surfaces; `my_agenda` for "what's on my plate today";
  and the agent/approval tools to see and decide pending actions.

## Rules

- `run_tool`, `find_tools`, `find_forms`, `find_app_templates` and
  `search_marketplace` work before the user signs in.
  Everything that touches their workspace asks them to connect their Xenition
  account first; when that happens, tell them why in one line.
- Act only on the signed-in user's own workspace. Never invent artifact ids —
  find the right item with `search_artifacts` first.
- Long-running work (agent runs, 3D generation, videos, app builds and deploys) happens in the background. The
  inline card shows live progress and fills in the result — do not claim it is
  finished before the card completes.
- Do not publish, share, or expose anything publicly unless the user explicitly
  asks (e.g. `create_shared_form` or a publish action).
- Prefer the tool that produces or reads real Xenition content over answering
  from memory when the user is asking about their own files or data.
