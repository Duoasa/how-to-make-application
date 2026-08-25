# DeepSeek Harness Adapter

| Field | Value |
|---|---|
| Status | Native compatibility; DeepSeek Harness is in developer preview |
| Verified | 2026-08-25 |
| Canonical skill | [`../SKILL.md`](../SKILL.md) |

DeepSeek Harness natively discovers directory bundles shaped as `<name>/SKILL.md` and loads explicitly referenced resources on demand. This repository already matches that format, so the adapter documents discovery roots, invocation, and the compatibility boundary rather than duplicating the skill.

## Compatibility decisions

- Keep `name` in kebab-case and equal to the directory name.
- Keep `description` concise enough for the default model-facing catalog limit.
- Use only the shared frontmatter intersection: `name` and `description`. Omitted invocation controls default to model-invocable and user-invocable.
- Keep resources explicitly linked from `SKILL.md`; DeepSeek Harness resolves only referenced resources instead of enumerating the bundle.
- Do not add account, model, tool, or provider assumptions to the canonical workflow.
- Treat `agents/openai.yaml` as Codex-only metadata. DeepSeek Harness ignores it.
- Recheck this adapter against upstream before future releases because DeepSeek Harness is still in developer preview and may introduce compatibility-breaking changes.

## Personal installation

Install under the default DSH home:

```bash
mkdir -p ~/.dsh/skills
git clone https://github.com/Duoasa/how-to-make-application.git ~/.dsh/skills/how-to-make-application
```

Update an existing personal installation:

```bash
git -C ~/.dsh/skills/how-to-make-application pull --ff-only
```

DeepSeek Harness also scans the shared agent root:

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/Duoasa/how-to-make-application.git ~/.agents/skills/how-to-make-application
```

## Project installation

Track the skill with the project as a Git submodule:

```bash
mkdir -p .dsh/skills
git submodule add https://github.com/Duoasa/how-to-make-application.git .dsh/skills/how-to-make-application
```

DeepSeek Harness also scans `<projectRoot>/.agents/skills`. The project root is the nearest ancestor containing `.git`; without one, it uses the current working directory.

## Invocation

Invoke it directly in Web, TUI, or ACP clients:

```text
/how-to-make-application Turn this app idea into a focused first-release plan.
```

The model may also select it automatically from the available-skills catalog and load it through the `skill` tool using the exact name `how-to-make-application`.

## Verification

1. Confirm `~/.dsh/skills/how-to-make-application/SKILL.md`, `~/.agents/skills/how-to-make-application/SKILL.md`, or the corresponding project path exists.
2. Start a DeepSeek Harness session whose working directory resolves to the intended project root.
3. Open the `/` skill catalog and confirm `how-to-make-application` appears.
4. Invoke it with a planning-only request first and confirm the complete skill content is injected.
5. Confirm referenced files under `references/` remain available on demand.

## Official references

- [DeepSeek Harness: Skills subsystem](https://github.com/deepseek-ai/deepseek-harness/blob/master/docs/subsystems/skills.md)
- [DeepSeek Harness: Filesystem skill provider](https://github.com/deepseek-ai/deepseek-harness/blob/master/packages/skill/skill-filesystem/README.md)
- [DeepSeek Harness developer preview](https://www.deepseek.com/harness/en/)
