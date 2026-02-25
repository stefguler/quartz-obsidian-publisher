# BMAD Method

## Quick Summary
BMAD (Breakthrough Method for Agile AI-Driven Development) is a role-based, agent-assisted workflow for building software through structured phases: strategy, planning, architecture, then implementation.

## What It Is
BMAD is a methodology that combines:
- predefined AI agent roles (for example analyst, PM, architect, developer)
- document-first planning artifacts (PRD, architecture, stories)
- iterative execution loops where each role contributes in sequence

## What It Does
- Translates high-level ideas into structured plans and implementable stories.
- Encourages separation of concerns across planning, design, and coding.
- Supports both web-based and IDE-based workflows through templates/tooling.

## What It Is Used For
- Teams or solo builders who want stronger structure than ad-hoc prompting.
- Medium/large projects where requirements and architecture quality matter.
- Situations where traceability from idea -> spec -> code is important.

## Strengths
- Clear role separation reduces context chaos.
- Strong planning phase improves implementation quality.
- Scales better than single-agent "do everything" prompting.
- Good for repeatable delivery workflows.

## Limits / Tradeoffs
- Heavier process overhead for small quick tasks.
- Requires discipline to maintain artifacts and flow.
- Can feel slower at the start due to planning depth.
- Not a security control by itself: in sensitive environments, unsafe outcomes are still possible without strict sandboxing, least-privilege access, and approval gates. Even with good planning artifacts, an agent can still run high-impact commands, access sensitive data, or make external changes if runtime permissions are broad.

## Source Links
- Official BMAD Method Specification: https://bmadcodes.com/bmad-method/
- Official BMAD User Guide: https://bmadcodes.com/user-guide/
