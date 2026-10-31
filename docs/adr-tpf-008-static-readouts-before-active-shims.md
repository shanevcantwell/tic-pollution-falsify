# Recipient transfer stub — proposed ADR-TPF-008

## Source handle

- Private source: `inbox/adr-tpf-008-static-readouts-before-active-shims.md`
- SHA-256: `e6ee3ba84db02a4efdb1591208a87289256f979f8eba1aca77224c5c998c075f`
- Declared status: **proposed, model-drafted, unratified; no H0 tested; no repair or implementation authorized**.

## Triage clauses

- Preserve ADR-TPF-006's on-policy behavioral comparison and ADR-TPF-007's earned/lazy endpoint as the primary study.
- Require a repeatable behavioral signal before mechanism localization; compare fixed external readouts, accessible internal readouts, and causal edits in that order.
- Advance only through preregistered practical-effect, control, uncertainty, and collateral-damage gates.
- Treat probe separation and geometric concentration as measurements, not causal proof or evidence that a correction is safe.
- Keep a fixed edit, a conditional controller, and no intervention as live alternatives; an active shim is not the default outcome.

## Dependencies and supersession

- Decision authority: ADR-TPF-005.
- Primary instrument: ADR-TPF-006.
- Primary endpoint: ADR-TPF-007.
- Earlier ADR-TPF-001/002/003 status must remain unchanged by this proposal.
- Supersedes: none. Superseded by: none known.
- Owning issue: create and link a dedicated proposed-ADR issue before opening the PR; the read-only target check found no existing ADR-TPF-008 path.

## Acceptance and falsification gates

- Accept for recipient triage only if `ADR-TPF-008` is unoccupied, dependencies and non-supersession are preserved, and the PR remains proposed/unratified.
- Do not advance a mechanism branch without a reproduced discriminating signal and relevant negative controls.
- Stop a fixed-readout or intervention branch when uncertainty excludes the preregistered useful effect, controls fail, or collateral damage exceeds its declared budget.
- A simpler fixed method defeating a conditional method falsifies the need for an active shim for the tested scope; failure of both does not establish that a more complex shim will work.

## Publication and ratification boundary

This artifact is a bounded recipient-transfer stub, not the private source body and not a canonical ADR. Only this stub may accompany the proposed PR. **Full source-body transfer or publication requires separate publication authorization.** Merge, numbering, status promotion, experiment execution, and remediation remain blocked until explicit operator/recipient HITL ratification under ADR-TPF-005.
