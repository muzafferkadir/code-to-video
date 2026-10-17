# code-to-video

A Claude Code skill that reads your repository and turns it into a narrated, animated explainer video using the [Higgsfield MCP](https://higgsfield.ai/mcp).

Point it at a project and it will:

1. Read the code, README and git history, and write a fact-checked brief.
2. Let you pick a video: **Intro** (30 s), **How it works** (60 s) or **Changelog** (30 s).
3. Write a scene-by-scene script for your approval.
4. Animate it in the style you choose (Whiteboard Doodle, Claymotion, Pixel Art, Stickman, …) and drop the MP4 into `video/`.

## Setup

1. Connect Higgsfield to Claude Code:

   ```sh
   claude mcp add --transport http -s user higgsfield https://mcp.higgsfield.ai/mcp
   ```

   Then run `/mcp` in Claude Code → `higgsfield` → Authenticate.

2. Install the skill:

   ```sh
   git clone https://github.com/muzafferkadir/code-to-video ~/.claude/skills/code-to-video
   ```

## Usage

Open Claude Code in any repository and type:

```
/code-to-video
```

Generation uses your Higgsfield credits; the cost is shown before anything is generated.

## License

MIT
