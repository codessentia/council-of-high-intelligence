# Council of High Intelligence

<p align="center">
  <img src="assets/header.jpeg" alt="Council of High Intelligence" width="800">
</p>

<p align="center">
  Structured multi-perspective deliberation for decisions that deserve more than one reasoning path.
</p>

<p align="center">
  <a href="https://github.com/codessentia/council-of-high-intelligence/actions/workflows/lint.yml"><img src="https://github.com/codessentia/council-of-high-intelligence/actions/workflows/lint.yml/badge.svg" alt="Lint"></a>
  <a href=".claude-plugin/plugin.json"><img src="https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fraw.githubusercontent.com%2Fcodessentia%2Fcouncil-of-high-intelligence%2Fmain%2F.claude-plugin%2Fplugin.json&query=%24.version&label=plugin&color=blue" alt="Plugin version"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue" alt="License"></a>
</p>

<p align="center">
  Claude Code · Codex · Gemini CLI · OpenCode
</p>

The council assigns a hard question to deliberately different analytical personas, keeps
their first positions independent, forces direct disagreement, and returns a verdict that
preserves unresolved questions, dissent, kill criteria, and the next concrete action.

## Try a council

The repository is a Claude Code plugin and its own marketplace. Register the marketplace
once, then install the plugin:

```bash
claude plugin marketplace add codessentia/council-of-high-intelligence
claude plugin install council@council-of-high-intelligence
```

The same two steps work from inside a session:

```text
/plugin marketplace add codessentia/council-of-high-intelligence
/plugin install council@council-of-high-intelligence
```

Start a new session (or run `/reload-plugins`) and convene the full council, a faster
panel, or a two-member dialectic:

```text
/council Should we open-source our agent framework?
/council --quick Should we add caching here?
/council --duo Should we use microservices or a monolith?
```

`/council` is the short form of `/council:council`; use the long form if another plugin
also claims `/council`. The 18 members install as subagents too — call one directly with
`@agent-council:council-socrates`, or let Claude pick one from its description.

To try a checkout without installing anything, load it for a single session:

```bash
git clone https://github.com/codessentia/council-of-high-intelligence.git
claude --plugin-dir ./council-of-high-intelligence
```

For Codex, Gemini CLI, or OpenCode, clone once and use the matching installer flag:

```bash
git clone https://github.com/codessentia/council-of-high-intelligence.git
cd council-of-high-intelligence

./install.sh --codex-only
./install.sh --gemini-only
./install.sh --opencode-only
```

Restart the target client after installation. The command remains `/council` on every
supported host.

## Use it for the decision boundary

Good council questions have material downside, competing values, incomplete evidence, or
an irreversible choice. Write down the decision, constraints, evidence, reversibility, and
deadline before adding personas.

![Decision field notes](assets/decision-field-notes.jpeg)

The field notes distinguish facts from inference, assumptions, and unknowns. They also make
it harder to use a long deliberation as decoration for a decision already made.

### When to use something smaller

- Use a direct answer or primary documentation for factual lookups.
- Run an experiment when the choice is cheap and reversible.
- Use `--quick` when cross-examination will not change the outcome.
- Use `--duo` when one tension matters more than broad coverage.
- Do not convene a council to manufacture support for a preferred answer.

## Choose a mode

| Mode | Shape | Use it when |
|---|---|---|
| Full | Independent analysis, cross-examination, final stance, synthesis | Stakes are high and competing frames need contact |
| Quick | Restate, rapid analysis, final positions | The decision needs breadth but not a full adversarial round |
| Duo | Opening positions, direct response, final statements | One polarity defines the decision |

![Council mode selector](assets/mode-selector.jpeg)

```text
/council --full What is the right pricing model?
/council --quick --triad shipping Should we release today?
/council --duo --members torvalds,ada Is this abstraction worth it?
```

Named triads select three relevant lenses without assembling the whole council:

```text
/council --triad strategy Where is our defensible advantage?
/council --triad risk What could make this launch irreversible?
/council --triad ai-product Which capability belongs in the product?
```

Available domains include `architecture`, `strategy`, `ethics`, `debugging`, `risk`,
`shipping`, `product`, `founder`, `ai`, `ai-product`, `ai-safety`, `decision`, `systems`,
`uncertainty`, `design`, `economics`, and `bias`. The canonical routing table lives in
[`skills/council/SKILL.md`](skills/council/SKILL.md).

## What the protocol protects

The full protocol has a fixed round budget. Members first restate the problem, analyze
blind, cross-examine other positions, declare a final stance, and then enter synthesis.
Enforcement checks look for premature agreement, repeated claims, missing dissent, and
unsupported confidence.

![Verdict blueprint](assets/verdict-blueprint.jpeg)

Verdicts lead with what remains unresolved. A recommendation is paired with acceptable
compromises, kill criteria, and one concrete next step. When the weighted tally remains
split, the result returns that split to the user instead of turning it into prose consensus.

Evidence labels separate:

- `FACT`: directly supported by supplied or retrieved evidence;
- `INFERENCE`: follows from evidence but is not directly observed;
- `ASSUMPTION`: required for the argument and still unverified;
- `UNKNOWN`: missing information that could change the decision.

## Track the outcome

A verdict is useful only if it can be checked later. Before acting, record the prediction,
owner, review date, and evidence that would change the recommendation. At the checkpoint,
mark the result confirmed, revised, reversed, or inconclusive instead of rewriting the
original rationale.

![Council outcome ledger](assets/outcome-ledger.jpeg)

## The 18 lenses

Members are analytical instruments, not impersonation claims. Each persona has a grounding
protocol, a method, known blind spots, and a structured response contract.

![Council panel composition](assets/panel-composition.jpeg)

| Member | Primary lens | Useful counterweight |
|---|---|---|
| Aristotle | Categories and structure | Lao Tzu on emergence and excess structure |
| Socrates | Assumption destruction | Feynman on reconstruction from first principles |
| Sun Tzu | Terrain and adversarial strategy | Aurelius on internal control and moral cost |
| Ada Lovelace | Formal systems and abstraction | Machiavelli on incentives and informal power |
| Marcus Aurelius | Resilience and moral clarity | Sun Tzu on external competition |
| Machiavelli | Power and incentives | Ada on formal consistency |
| Lao Tzu | Non-action and emergence | Aristotle on explicit categories |
| Richard Feynman | Explanation and empirical debugging | Socrates on the premise itself |
| Linus Torvalds | Shipping and maintainability | Meadows on system-level consequences |
| Miyamoto Musashi | Timing and decisive action | Torvalds on acting before the ideal moment |
| Alan Watts | Reframing and false problems | Torvalds on concrete implementation |
| Andrej Karpathy | Empirical ML behavior | Sutskever on frontier risk |
| Ilya Sutskever | Scaling and AI safety | Karpathy on observation and iteration |
| Daniel Kahneman | Cognitive bias | Feynman on explicit causal reasoning |
| Donella Meadows | Feedback loops and high-impact interventions | Torvalds on local fixes |
| Charlie Munger | Inversion and model lattices | Aristotle on single-system classification |
| Nassim Taleb | Tail risk and fragility | Karpathy on smooth empirical trends |
| Dieter Rams | User clarity and restraint | Ada on what can be formalized |

The repository stores each member contract under [`agents/`](agents/). Custom panels can
use `--members`, named triads, or the `classic`, `exploration-orthogonal`, and
`execution-lean` profiles documented in [`skills/council/SKILL.md`](skills/council/SKILL.md).

## Multi-provider routing

The detection script checks which supported providers are available, then the coordinator
distributes seats across them. Polarity pairs are separated when possible so a single model
family does not play both sides of a disagreement.

![Council provider routing](assets/provider-routing.jpeg)

| Provider path | Detection |
|---|---|
| Native host subagents | Available through the active supported client |
| OpenAI | `codex` executable |
| Google | `gemini` executable |
| Ollama | `ollama` executable |
| NVIDIA NIM | `NVIDIA_API_KEY` |
| Cursor | `cursor-agent` executable or configured login |

Preview routing without running a council:

```text
/council --dry-route --triad decision Should we accept this acquisition offer?
```

Use `--no-auto-route` to keep native-host defaults. Use `--models <path>` with a copy of
[`configs/provider-model-slots.example.yaml`](configs/provider-model-slots.example.yaml)
for an explicit seat map. Provider failure is reported before the seat falls back to the
native host.

## Installation reference

The plugin install above is the recommended path for Claude Code: it keeps the council
current through `claude plugin update`, namespaces the agents, and writes nothing into
`~/.claude/agents/`. `install.sh` remains for the other hosts and for Claude Code setups
that cannot use plugins; it copies `skills/council/SKILL.md`, the agents, and the
detection script into the host's config directory.

```bash
./install.sh                         # Claude Code (copy into ~/.claude, no plugin)
./install.sh --codex                 # Claude Code + Codex
./install.sh --codex-only            # Codex only
./install.sh --gemini                # Claude Code + Gemini CLI
./install.sh --gemini-only           # Gemini CLI only
./install.sh --opencode              # Claude Code + OpenCode
./install.sh --opencode-only         # OpenCode only
./install.sh --copy-configs          # Include provider-routing templates
./install.sh --dry-run               # Preview writes
```

Custom target directories are supported through `--claude-dir`, `--codex-dir`,
`--gemini-dir`, and `--opencode-dir`. Run `./install.sh --help` for the current contract.

## Verify the checkout

```bash
claude plugin validate .
./scripts/council-simulation-checklist.sh
./scripts/validate-roster.py
./install.sh --dry-run --codex
./install.sh --dry-run --gemini
./install.sh --dry-run --opencode
```

`claude plugin validate` reads the manifests, the skill, and the agent frontmatter the way
the plugin loader does. The checklist validates persona structure, host-protocol parity,
routing configuration, execution checkpoints, verdict fields, and installer behavior. Use
the [demo session pack](demos/session-pack.md) to exercise full, quick, and duo modes.

## Repository map

```text
.claude-plugin/plugin.json       Claude Code plugin manifest
.claude-plugin/marketplace.json  marketplace entry so the repo installs itself
skills/council/SKILL.md          canonical coordinator protocol — the /council skill
agents/                          18 grounded persona contracts — the plugin's subagents
SKILL.codex.md                   Codex host mirror
SKILL.gemini.md                  Gemini CLI host mirror
SKILL.opencode.md                OpenCode host mirror
configs/                         provider and model-routing examples
demos/                           sample sessions and verdict template
scripts/                         detection, conversion, and validation tools
assets/                          brand system and README visuals
install.sh                       multi-host installer (non-plugin path)
```

Protocol changes start in `skills/council/SKILL.md` and must remain behaviorally aligned
with each host mirror. See [CONTRIBUTING.md](CONTRIBUTING.md) for the required checks and review contract.
Security reports belong in [SECURITY.md](SECURITY.md), not a public issue.

## Project links

This repository is a fork of
[0xNyk/council-of-high-intelligence](https://github.com/0xNyk/council-of-high-intelligence)
that finishes the Claude Code plugin packaging (a real skill file, plugin-root asset
paths) and publishes it through its own marketplace. The protocol, the personas, and the
brand are the upstream author's work.

- [Release history](CHANGELOG.md)
- [Brand kit](assets/BRAND.md)
- [Upstream project](https://github.com/0xNyk/council-of-high-intelligence) · [OSS profile](https://www.nyk.dev/oss/council-of-high-intelligence)
- [Sponsor the upstream maintainer](https://github.com/sponsors/0xNyk)
- [Upstream maintainer: Nyk](https://nyk.dev) · [@nykdotdev](https://x.com/nykdotdev)
- [Upstream issues](https://github.com/0xNyk/council-of-high-intelligence/issues)

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="assets/star-history-dark.svg">
    <img src="assets/star-history-light.svg" alt="Council of High Intelligence star history" width="600">
  </picture>
</p>

## License

[MIT](LICENSE) © 2026 [0xNyk](https://github.com/0xNyk)
