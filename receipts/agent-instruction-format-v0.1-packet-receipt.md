# Packet Receipt — agent-instruction-format-v0.1

This is a public receipt for the v0.1 instruction packet artifacts introduced in
this change. It records what was produced, its status, and the non-canon
posture. It is not a private operational receipt.

## Receipt

- **Packet schema:** `schemas/agent-instruction-format-v0.1.json`
- **Schema version:** v0.1
- **Packet status:** candidate
- **Issuer:** hummbl-dev/agent-instruction-format
- **Non-canon:** true

## Artifacts produced

- `docs/v0.1-boundary.md` — scope, non-goals, adoption boundary, review
  expectations, non-canon posture, required packet pieces, adjacent repo links.
- `docs/prior-art.md` — public prior art and adjacent ecosystem references.
- `schemas/agent-instruction-format-v0.1.json` — JSON Schema for a v0.1 packet.
- `examples/instruction-packet-v0.1.example.json` — worked example packet.
- `fixtures/valid/instruction-packet-v0.1.valid.json` — valid fixture.
- `fixtures/invalid/instruction-packet-v0.1.invalid.json` — invalid fixture
  (missing required `instructionContract`).

## Issues addressed

- #1 Define v0.1 scope and boundary
- #2 Collect prior art and adjacent ecosystem references
- #3 Design minimal schema/examples layout

## Reviewer confirmation

- [x] Scope is understood.
- [x] No secrets or private operational content are present.
- [x] Packet is candidate status, not adopted guidance.
- [x] No concept is canonized by this packet.

## Validation

The valid fixture is expected to pass validation against
`schemas/agent-instruction-format-v0.1.json`. The invalid fixture is expected to
fail validation because it omits the required `instructionContract` field.
