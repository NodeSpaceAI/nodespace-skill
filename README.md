# nodespace-skill

The NodeSpace [Agent Skill](https://agentskills.io) — import this repo into
Claude Code, Codex, Gemini CLI, OpenCode, or any other Agent-Skills-compatible
harness to give it direct access to the [NodeSpace](https://nodespace.app)
knowledge graph.

**This is a generated publish target, not a place to edit.** Its content is
rendered from [`NodeSpaceAI/nodespace-core`](https://github.com/NodeSpaceAI/nodespace-core)'s
`packages/skill` and pushed here by that repo's release pipeline
(`scripts/publish-skill-repo.ts`) on every release. A hand edit made directly
in this repo does not survive the next release — it's overwritten, not
merged. If something here needs to change, change it in `nodespace-core` and
cut a release.

The Homebrew tap ([`homebrew-nodespace`](https://github.com/NodeSpaceAI/homebrew-nodespace))
went two months stale under hand maintenance before this pattern replaced it
— this repo exists so the skill can't repeat that failure mode.

## Install

```
skills/nodespace/
```

is a self-contained skill folder. Copy or symlink it into your harness's
skills directory:

```bash
git clone https://github.com/NodeSpaceAI/nodespace-skill.git /tmp/nodespace-skill
cp -r /tmp/nodespace-skill/skills/nodespace ~/.claude/skills/nodespace       # Claude Code
cp -r /tmp/nodespace-skill/skills/nodespace ~/.codex/skills/nodespace       # Codex
cp -r /tmp/nodespace-skill/skills/nodespace ~/.gemini/skills/nodespace     # Gemini CLI
cp -r /tmp/nodespace-skill/skills/nodespace ~/.opencode/skills/nodespace   # OpenCode
```

`skills/nodespace/SKILL.md` carries the required `name` + `description`
frontmatter (plus the optional `allowed-tools` and `compatibility` fields the
spec defines) and `skills/nodespace/references/cli.md` is the on-demand CLI
reference it links to — nothing else is required.

The skill drives the `nodespace` CLI, so it needs the CLI on `$PATH` and the
`nodespaced` daemon running. Install NodeSpace itself via the
[desktop app](https://nodespace.app) or:

```bash
curl -fsSL https://nodespace.ai/install.sh | sh
```

## Not on npm

`@nodespaceai/skill` is not published to npm, and this repo is not a
complement to an npm package — it's the replacement. The NodeSpace desktop
app installs the skill itself, directly, without a registry; this repo is
the distribution channel for every other harness.

## Versioning

`SKILL.md`'s `compatibility` field records the NodeSpace app version the
current revision targets, stamped in from the release that published it.
