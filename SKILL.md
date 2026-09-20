---
name: quality-policy
description: >-
  Apply quality checks to delegated code changes: acceptance criteria, implementer
  verification, integration checks, and independent review of the completed task.
  Use when coordinating implementation or accepting work from multiple agents
  within an existing orchestration workflow.
---

# Quality Policy

Verify the outcome. Scale the depth of verification to the change and its risks.

## Fit the existing workflow

Use the active orchestration workflow to assign work, exchange findings, and
report completion. Apply these requirements at its existing handoff and acceptance
points, using its tools, permissions, and reporting format. Count equivalent
checks and reviews already performed; retain stricter project requirements.

The **orchestrator** owns acceptance of the whole task. **Implementers** own their
assigned changes and self-checks. The **reviewer** independently assesses the
completed task. Pass applicable requirements with each assignment so recipients
can fulfill their role from the context they receive. Each participant follows
the checkpoints relevant to that role; the orchestrator arranges review.

## 1. Before implementation: define acceptance

**Orchestrator:** establish the intended outcome, scope, constraints, and observable
acceptance criteria. Use the available context for straightforward changes;
resolve consequential ambiguity before dependent work. Keep criteria anchored to
the requested behavior and explain any agreed change to them.

**Ready when:** each implementer knows their scope and how to demonstrate success.

## 2. Before handoff: verify the assigned result

**Implementer:** start with the changed scenario and its direct dependencies.
Expand checks when a concrete risk or project requirement calls for it. Verify
behavior and meaningful effects: a successful build establishes buildability;
a save operation requires checking the persisted state.

For a bug fix, reproduce the failure when feasible and add a regression test that
protects the corrected behavior. Derive test expectations from the intended
behavior; justify changed snapshots or fixtures against that behavior. Use the
project's existing test tools and authorized environments and data.

### UI changes

Inspect the actual rendered result for visual changes. For interaction changes,
follow the ordinary user path and inspect both the resulting state and its
appearance. Use browser or application automation available in the environment.

Select checks by impact: inspect affected styling for a cosmetic change; exercise
keyboard and focus behavior for a changed control; check relevant viewport sizes
for layout changes. Include long content and other edge states when the change
puts them at risk. Use ordinary interaction to establish usability, screenshots
to assess appearance, and state assertions to establish behavior. Add permanent
end-to-end tests when their regression value warrants the maintenance cost.

### Evidence at handoff

Report the checked revision or working state, scenario or command, observed
result, and useful artifacts in the workflow's existing format. Keep evidence
concise and safe to share. Identify mocked boundaries, unavailable checks, and
environment limitations. Support claims of pre-existing failures with evidence.

**Handoff complete when:** the assigned work and applicable self-checks are done,
or an explicit blocker is returned to the orchestrator. Distinguish implementation
status from verification status. The implementer can finish their assignment at
handoff; the orchestrator owns the remaining acceptance work.

## 3. After integration: verify the combined result

**Orchestrator:** collect the implementers' results and check the combined change
against task acceptance criteria. Exercise interactions between their changes
where integration creates risk. Reuse evidence that still applies and refresh
checks invalidated by merging, conflict resolution, or later edits. Ensure tests
and running applications reflect the intended working copy and current change.

**Ready for review when:** all assigned implementation work is accounted for, the
combined diff is stable, and verification results and limitations are available.

## 4. Before acceptance: review the completed task once

**Orchestrator:** send the combined task diff, acceptance criteria, relevant
context, and verification evidence to one independent reviewer. Schedule this
review after implementation and integration, at the boundary of the whole task.
Individual file edits and intermediate implementer handoffs use self-checks.
Count an equivalent existing independent review toward this checkpoint, while
honoring any additional reviews required by the project.

A reviewer may be an agent or a human independent of authorship; using a different
model is optional. The review assignment is assessment: identify material defects
and verification gaps within the task's scope, and return findings to the
orchestrator for resolution.

For each blocking finding, state the violated requirement and supporting scenario,
test, or clear code reasoning. Separate confirmed blockers, uncertainties needing
a targeted check, optional improvements, and unrelated findings. Report serious
unrelated risks separately for the owner to triage.

**Review complete when:** the reviewer has assessed the combined task and returned
actionable findings or an explicit result with no blocking findings. If independent
review is unavailable, record the missing acceptance requirement and route it to
the task owner for resolution or an authorized exception.

## 5. After findings: close blockers with targeted follow-up

**Orchestrator:** collect blocking findings into a focused correction pass. Have
the responsible implementers fix them or provide evidence that resolves them.
Check the affected scenarios and consequences of the correction diff. Use the
same reviewer to confirm closure where independence is preserved, reusing the
unaffected review and verification results.

Keep follow-up scoped to the findings and corrections. A full review restarts only
when the scope changes substantially or the project requires it. Optional polish
can remain optional. Repeated failure without new evidence calls for reassessing
the approach and escalating a concrete blocker when needed. If the reviewer
authors a correction, obtain an independent assessment of that correction.

**Ready for acceptance when:** each blocker is fixed and verified, resolved by
evidence, or covered by an explicitly authorized exception.

## 6. At completion: report acceptance honestly

**Orchestrator:** accept the task when its criteria are met, required checks and
independent review apply to the final result, and blockers are resolved. Record
authorized exceptions as exceptions and distinguish passed, failed, and unperformed
checks. Report the outcome, evidence, remaining limitations, and separate findings
through the workflow's native completion contract.

For text-only work, validate meaning, accuracy, and references with checks suited
to the document and project. Apply code and UI checkpoints when those surfaces
are affected.
