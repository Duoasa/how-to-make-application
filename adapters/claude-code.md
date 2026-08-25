# Claude Code Adapter

| Field | Value |
|---|---|
| Status | Native compatibility |
| Verified | 2026-08-25 |
| Canonical skill | [`../SKILL.md`](../SKILL.md) |

Claude Code natively supports directory-based Agent Skills with a `SKILL.md` entrypoint and optional supporting resources. This repository already uses that portable structure, so the adapter contains discovery and invocation guidance rather than a second copy of the skill.

## Compatibility decisions

- Keep `name` in kebab-case and equal to the directory name.
- Keep routing guidance in `description`; Claude Code uses it for automatic selection.
- Keep detailed material in explicitly linked `references/` files for progressive disclosure.
- Do not add `allowed-tools`: this workflow must not pre-approve shell, write, publishing, or other side effects.
- Treat `agents/openai.yaml` as Codex-only metadata. Claude Code ignores it.
- Preserve one canonical body. Do not create a Claude-specific fork unless a future Claude capability materially changes the workflow itself.

## Personal installation

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Duoasa/how-to-make-application.git ~/.claude/skills/how-to-make-application
```

Update an existing personal installation:

```bash
git -C ~/.claude/skills/how-to-make-application pull --ff-only
```

## Project installation

Track the skill with the project as a Git submodule:

```bash
mkdir -p .claude/skills
git submodule add https://github.com/Duoasa/how-to-make-application.git .claude/skills/how-to-make-application
```

Claude Code discovers project skills from `.claude/skills/` in the current directory and parent directories up to the repository root.

## Invocation

Invoke it directly:

```text
/how-to-make-application Turn this app idea into a focused first-release plan.
```

Claude Code may also invoke it automatically when a request matches the frontmatter description.

## Verification

1. Confirm `~/.claude/skills/how-to-make-application/SKILL.md` or `.claude/skills/how-to-make-application/SKILL.md` exists.
2. Start Claude Code in the intended project.
3. Type `/how-to-make-application` and confirm it appears in completion.
4. Invoke it with a planning-only request first and confirm it distinguishes product intent, production reality, verification evidence, and human acceptance.
5. Confirm no tools are pre-approved by the skill.

## Official references

- [Claude Code: Extend Claude with skills](https://code.claude.com/docs/en/slash-commands)
- [Claude Agent SDK: Extend agents with skills](https://code.claude.com/docs/en/agent-sdk/skills)
