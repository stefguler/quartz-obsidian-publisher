# Agentic Coding Methods Comparison

## At a Glance
| Method | Type | Best For | Main Strength | Main Tradeoff |
|---|---|---|---|---|
| BMAD | Role-based methodology | Structured product/project delivery | Clear role separation + planning depth | More process overhead |
| Spec Kit | Spec-driven toolkit/workflow | Teams that want consistent engineering quality | Strong artifact pipeline and reproducibility | Upfront effort and discipline |
| Ralph Wiggum Loop | Informal anti-pattern / speed loop | Disposable prototyping and exploration | Maximum short-term velocity | High quality and safety risk |

## Product-Style Comparison
### 1) Workflow Structure
- BMAD: Strong staged process with defined agent roles.
- Spec Kit: Strong staged process centered on formal artifacts (`spec`, `plan`, `tasks`).
- Ralph Loop: Minimal process; repetition without robust gates.

### 2) Speed vs Quality
- BMAD: Balanced speed/quality, leaning quality through planning.
- Spec Kit: Quality and consistency first, speed comes after setup.
- Ralph Loop: Speed first, quality often deferred.

### 3) Team Scalability
- BMAD: Good for multi-role collaboration.
- Spec Kit: Excellent for repeatable team workflows and handoffs.
- Ralph Loop: Weak team scalability due to low traceability and review rigor.

### 4) Risk Profile
- BMAD: Medium risk if roles/artifacts are followed.
- Spec Kit: Lower risk for regressions and architecture drift.
- Ralph Loop: Higher risk for hidden defects, security mistakes, and rework.

## Recommendation by Use Case
- Choose **BMAD** when you want role clarity and robust agile execution.
- Choose **Spec Kit** when you want a consistent, spec-first engineering system.
- Use **Ralph Wiggum Loop** only for constrained prototypes/spikes, then transition quickly to BMAD or Spec Kit style rigor.

## Sources
- BMAD: https://bmadcodes.com/bmad-method/ and https://bmadcodes.com/user-guide/
- Spec Kit: https://developer.microsoft.com/blog/spec-driven-development-spec-kit and https://github.com/github/spec-kit
- Ralph Wiggum Loop: https://awesomeclaude.ai/ralph-wiggum
