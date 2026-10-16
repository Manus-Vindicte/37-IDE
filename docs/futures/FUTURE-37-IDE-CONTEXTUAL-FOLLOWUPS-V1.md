# FUTURE-37-IDE-CONTEXTUAL-FOLLOWUPS-V1

**Status:** FUTURE / NOT_SCHEDULED  
**Type:** UX capability candidate (not an implementation PT)  
**Area:** 37 IDE · Composer / Agent Chat  
**Priority:** DEFERRED (not part of SCM Workbench S1 or SCM-09)

## Intent

Add compact, context-aware **Follow-up / Suggested Action chips** directly below a completed agent response, e.g. `↳ Abnahmekriterien ergänzen` or `↳ Nächsten Slice prüfen`. They shorten the path from reading a result to sending the next relevant request.

## Preferred behavior

- Show 0–3 suggestions only when they are genuinely relevant; otherwise show none. Never occupy a permanent empty bar.
- Click inserts a proposed prompt into the Composer for inspection/editing, **not** an implicit tool call or autonomous action. Explicit send remains a separate user act. An optional explicit quick-send mode needs a separate UX decision.
- Derive suggestion labels and draft text from the current response/task context; avoid repetitive, generic chips and duplication of existing actions.
- Follow-up chips are not permissions. No direct file writes, shell calls, SCM operations, approvals, cloud egress, or bypass of TaskEnvelope / Bifrost / Gatekeeper.
- Preserve keyboard focus, accessibility labels, predictable ordering, and responsive wrapping. Respect reduced-motion and deterministic Golden-Markup requirements.

## Reuse / qualification before implementation

- Inspect the historical `SuggestionLayer` and its actual consumers. Previous audits categorized it as legacy / `REMOVE_LATER` after a zero-consumer finding; **do not assume it is active or reusable** without current source verification.
- Inspect existing Composer actions, message-footer components, chat action contracts, and suggestion/readmodel facilities first. Reuse existing primitives when practical; create no parallel recommendation engine by default.
- Prefer local, lightweight, deterministic suggestions as the baseline. Model-generated suggestions are an optional later variant, not required for V1.

## Acceptance sketch (for a future implementation slice)

1. Relevant completed message shows up to three actionable chips; irrelevant message shows none.
2. Selecting a chip yields a visible editable Composer draft, without execution or authorization side effects.
3. Missing context / unavailable engine fails closed without ghost buttons.
4. Golden-Markup and accessibility checks pass; UI is responsive and keyboard-operable.
5. No regression in existing Composer, TaskEnvelope, approval, or agent-run flows.

## Scheduling boundary

This is **one future idea**, not a new policy, immediate task, or authorization. No changes to SCM Workbench S1, SCM-09, governance contracts, or production UI are requested. Promote to a scoped PT only when the Composer/Chat UX backlog is prioritized and current code consumers have been re-audited.
