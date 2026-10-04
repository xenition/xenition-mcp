---
name: explainer-video
description: Use when the user wants a short explainer, product promo, social clip or narrated video about a topic, product or idea, made with Xenition's media tools (create_video, create_speech, create_image, edit_video).
---

# Explainer video with Xenition

Xenition makes the parts of an explainer — clips, stills, a voiceover — and
improves finished footage. It does **not** yet join several clips and a
voiceover into one edited video; say so up front and hand the user the parts,
or make a single clip when that is enough.

## 1. Script first, in the chat

Write a script of 3–6 scenes. For each scene: one line of narration (about 2
seconds per 5 words) and one line of what is on screen. Keep the whole piece
under 60 seconds unless asked. Show it and let the user change it before
spending credits.

## 2. Voiceover

Call `create_speech` once with the full narration (language if not English).
Share the audio link.

## 3. Visuals, one per scene

- Motion: `create_video` per scene with a visual prompt that names subject,
  camera and style, 5–10 seconds, the same aspect for every scene (portrait
  for Reels/TikTok/Shorts, landscape otherwise). Keep the style words
  identical across scenes so they match.
- Stills are faster and cheaper: `create_image` per scene when the user wants
  a slideshow-style explainer or is watching cost.

Videos take a few minutes. Start them, tell the user, and check each with
`video_status` when they ask — do not claim they are ready before it says so.

## 4. Finishing a recorded video

For footage the user already has (a screen recording, a talking-head clip),
`edit_video` adds burned-in captions, cleans up picture and sound, removes the
background, or cuts out silences. Captions need the spoken language.

## 5. Hand-off

List every part with its link, in scene order, next to its narration line, so
the user can assemble them in the Xenition video editor or any editor.

## Limits

Xenition cannot post to social networks or send media anywhere. Do not use real
people's faces, voices or brands without the user confirming they have the
rights.
