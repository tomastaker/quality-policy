# Quality Policy

A small skill for quality assurance in distributed agent work. It adds acceptance
and verification checkpoints to the orchestration workflow you already use.

The key cadence is simple: implementers self-check their assignments, the
orchestrator verifies the combined result, and one independent reviewer assesses
the completed task before acceptance. Review findings lead to focused corrections
and targeted follow-up. Individual file edits stay within the implementer's
self-check loop.

## Use

The skill is self-contained in [SKILL.md](SKILL.md). Place this repository's
`quality-policy` folder in your environment's supported skill location, or make
`SKILL.md` available to the orchestrator as task instructions. Follow that
environment's loading mechanism.

For example, clone it into a skill location you have chosen:

```sh
git clone https://github.com/tomastaker/quality-policy.git /path/to/skills/quality-policy
```

Ask the orchestrator:

> Apply quality-policy to this task. Pass the relevant acceptance criteria and
> self-check requirements to each implementer. Once their changes are integrated,
> arrange one independent review of the completed task before accepting it.

## Example

Two implementers work on a settings feature: one changes the form, the other
changes persistence. Each verifies their assigned behavior and returns evidence.
The orchestrator checks that submitting the form persists the value and that
reopening it displays the saved value, then sends the combined diff for review.
If review finds a validation defect, the responsible implementer corrects it and
the reviewer checks that correction and its effects.

## Scope

The skill defines quality responsibilities and completion criteria. Scheduling,
agent selection, isolation, messaging, and status reporting come from the host
workflow. Checks scale with the change's risk, and equivalent existing evidence
and reviews count toward acceptance. Project requirements and authorization
boundaries continue to apply.

This repository contains instructions only. Compatibility with a particular
orchestrator depends on its ability to load or pass those instructions; no
orchestrator-specific adapter is included.
