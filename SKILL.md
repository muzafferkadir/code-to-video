---
name: code-to-video
description: Turn a code repository into a narrated animated explainer video (product intro, how-it-works, or changelog) through the Higgsfield MCP. Use when the user says "code to video", "/code-to-video", "make a video from this repo/project", "repo'dan video", "kodumdan video çıkar", or wants a promo/explainer animation generated from source code.
---

# code-to-video

Read a repository, find the story worth telling, write a script, and have the Higgsfield MCP animate it.
You own the understanding and the script; Higgsfield's `faceless-video` workflow owns production.

## Rules

- Use the **Higgsfield MCP tools only** (`mcp__higgsfield__*`). Do not install or call the Higgsfield CLI.
- Every claim in the script must trace to a file in the repo. Never invent features, numbers, or users.
- Narration is written in the user's language unless they ask otherwise.
- Never start a paid generation before the user approves the script; the workflow shows the credit cost before spending.

## 1. Read the repo

Read, in this order, and stop once the story is clear:

1. `README*`, docs landing page, `package.json` / `Cargo.toml` / `pyproject.toml` / `go.mod` (name, description, homepage).
2. Entry points and top-level source dirs: what goes in, what comes out.
3. `git log --oneline -30` and the latest tag (`git describe --tags --abbrev=0`) for the changelog type.

Write `video/brief.md`:

```md
# <project>
- Pitch: <one sentence, plain words>
- For: <who has this problem>
- Problem: <what hurts without it>
- Features: <3 bullets, each with the file that proves it>
- Flow: <input → step → step → output, 4-6 steps, each with a file path>
- Links: <site / repo URL>
```

## 2. Pick the video

Ask once, with these defaults pre-selected:

| Type | Length | Built from |
|---|---|---|
| **Intro** (default) | 30 s | Pitch, Problem, Features |
| **How it works** | 60 s | Flow |
| **Changelog** | 30 s | Commits since the previous tag |

Then show the style options from `get_explainer_presets` (name only, 6 at most; suggest Whiteboard Doodle, Claymotion, Pixel Art, Stickman Cartoon, Paper Diorama, Isometric Flat Vector). Aspect defaults to 16:9.

## 3. Write the script

Write `video/<type>/script.md`: a title, then one block per 10-second scene (30 s = 3 blocks, 60 s = 6).

```md
# <title>

## Scene 1
Narration: <one or two short sentences, about 2 words per second>
Visual: <what is on screen, concrete objects and motion, no text-heavy UI>
```

- Scene 1 is the hook: the problem or the result, never "Hello, this is…".
- One idea per scene. Turn code concepts into objects: a file is a box, a request is a letter, silence is a flat line.
- The last scene names the project and its link.

Show the script and wait for approval or edits.

## 4. Produce

1. Call `get_workflow_instructions({ workflow: "faceless-video" })` and follow it.
2. Hand it every intake answer up front so it runs straight to delivery: type **Explainer**, motion mode **animated**, the chosen style, duration, aspect, subtitles **on**, thumbnail **no**, and the approved script as a **pasted script** with its title. Only the voice picker is left for the user.
3. Save the final MP4 to `video/<type>/<style-slug>.mp4` and append the credits spent to `video/log.md`.

## 5. Variations

Same script, another style: reuse `script.md` unchanged and run step 4 again with the new style. Compare the results side by side in the chat.
