# Research Mode for Claude Code

Anti-hallucination toggle for Claude Code. Activates constraints from [Anthropic's documentation](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) that force Claude to cite sources, say "I don't know" when unsure, and ground responses in direct quotes.

## Install

```bash
claude plugin marketplace add gdodd1977/research-mode
claude plugin install research-mode
```

Restart Claude Code after installing.

## Use

```
/research-mode:research
```

Or with a topic:

```
/research-mode:research what caused the Change Healthcare breach
```

Say "exit research mode" to turn it off.

## What it does

Four constraints activate simultaneously:

1. **Say "I don't know"** — no guessing, no inferring. If there's no credible source, Claude says so.
2. **Direct quotes for factual grounding** — responses are grounded in word-for-word quotes from source material, not paraphrased summaries.
3. **Verify with citations** — every claim must reference a file, URL, paper, or named source. Unsourced claims get retracted.
4. **External knowledge restriction** — only uses information from provided documents, project files, and web searches. No gap-filling from training data.

Advanced techniques (chain-of-thought verification, iterative refinement) are applied when appropriate.

## What it doesn't do

- Not always-on. It's a toggle. Turn it on for research, off for creative work.
- Not slow. Claude still uses tools in parallel and works efficiently.
- Not restrictive on new ideas. You can synthesize across sources, but inputs must be grounded.

## Why

LLMs hallucinate. When you're doing research that matters, you need guardrails that force citation discipline. This packages [Anthropic's own recommendations](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations) into a one-command toggle.

## Project structure

```
research-mode/
├── .claude-plugin/
│   └── marketplace.json        # Marketplace metadata
├── research-mode/
│   ├── .claude-plugin/
│   │   └── plugin.json         # Plugin metadata
│   └── commands/
│       └── research.md         # The command definition
├── LICENSE
└── README.md
```

## License

MIT
