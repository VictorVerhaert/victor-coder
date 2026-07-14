# victor-coder

> "Me think, why waste time say lot word, when few word do trick."

![](assets/kevin.jpg)

Executor-advisor agent trio for **VS Code Copilot** only.

**Pattern:** Sonnet main agent (Victor) handles all coding with minimal-code discipline. Opus advisory subagents fire only when needed — planner on complex tasks, reviewer after every code change.

## Agents

| Agent | Model | Visible | Role |
|-------|-------|---------|------|
| `Victor — Coder` | Claude Sonnet 4.6 | ✅ | Main coding agent — asks questions, minimal-code discipline, per-project memory |
| `Advisor — Plan` | Claude Opus 4.8 | ❌ subagent only | Deep planner for complex/ambiguous tasks |
| `Advisor — Review` | Claude Opus 4.8 | ❌ subagent only | Mandatory post-change reviewer (minimal-code lens + OWASP) |

## Install

### User-level (all workspaces)

```
copilot plugin marketplace add VictorVerhaert/victor-coder
copilot plugin install victor-coder@victor-coder
```

Or in an interactive Copilot CLI session:

```
/plugin marketplace add VictorVerhaert/victor-coder
/plugin install victor-coder@victor-coder
```

Then run **Chat: Reload Custom Agents** (`Ctrl+Shift+P`) in VS Code.

### Workspace-level (one repo)

Copy `agents/` to `.github/agents/` in your repo — VS Code auto-discovers them.

```bash
cp -r agents/ path/to/your-repo/.github/agents/
```

## Customise

- **Your name**: change `name:` in `agents/victor-coder.agent.md`.
- **Model**: swap model names in any `.agent.md` to match your Copilot subscription.
- **Tools**: extend the `tools:` list in `victor-coder.agent.md` with MCP servers (e.g. `io.github.tavily-ai/tavily-mcp/*`).
- **Memory**: agents read `/memories/repo/` — add project-specific notes there to persist knowledge across sessions.

## Inspired by

- [caveman](https://github.com/JuliusBrussee/caveman) — terse communication, minimal token usage
- [ponytail](https://github.com/DietrichGebert/ponytail) — minimal-code discipline, YAGNI ladder
