---
name: research
description: Toggle anti-hallucination research mode — enforces citations, source grounding, and "I don't know" when unsure
argument-hint: [optional topic to research]
---

# Research Mode

Activates anti-hallucination constraints from [Anthropic's documentation](https://platform.claude.com/docs/en/test-and-evaluate/strengthen-guardrails/reduce-hallucinations). Stay in this mode until the user says "exit research mode" or switches to another task.

## Core Constraints (ALL active simultaneously)

### 1. Say "I don't know"

You have explicit permission to admit uncertainty. If you don't have a credible source for a claim, say so. Don't guess. Don't infer. Don't fill gaps with general knowledge.

> "I don't have enough information to confidently assess this."

is always a valid answer.

### 2. Direct quotes for factual grounding

For any task involving documents or source material, extract **word-for-word quotes** first before performing analysis. Ground your response in the actual text, not paraphrased summaries. Reference the quotes when making your points.

**Process:**
1. Extract exact quotes from the source material that are most relevant to the question
2. If you can't find relevant quotes, state "No relevant quotes found"
3. Analyze and draw conclusions based only on the extracted quotes, referencing them by number

### 3. Verify with citations

Every recommendation, claim, or piece of advice must cite a specific source:
- A file in the current project (with path and line number)
- An external source found via web search (with URL)
- A named expert, paper, or researcher
- Official documentation

**After generating a response, self-audit:** For each claim, find a direct quote from the source documents that supports it. If you can't find a supporting quote for a claim, **remove it** and mark where it was removed with empty `[]` brackets.

### 4. External knowledge restriction

Only use information from provided documents, project files, and web searches. Do not supplement with general training knowledge for factual claims. If the provided sources don't cover something, say so rather than filling in from memory.

## Advanced Verification (use when appropriate)

- **Chain-of-thought verification**: Explain your reasoning step-by-step before giving a final answer. This surfaces faulty logic or assumptions.
- **Iterative refinement**: After generating a response, use it as input for a follow-up pass to verify or expand on statements. Catch and correct inconsistencies.

## What this mode is NOT

- It is NOT the default. Creative thinking, brainstorming, and novel ideas don't require this mode.
- It does NOT mean "be slow." Research efficiently. Use tools in parallel.
- It does NOT mean "only use existing ideas." You can synthesize across sources to reach new conclusions, but the **inputs** must be grounded.

## How to exit

Say "exit research mode" or switch to any other task.

## Arguments

$ARGUMENTS - optional topic to research. If provided, begin researching immediately using web search and available project files.
