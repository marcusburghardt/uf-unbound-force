## Why

The proposal template and schema instructions hardcode the
Unbound Force constitution principles (Autonomous Collaboration,
Composability First, Observable Quality, Testability). When
`uf init` deploys this template to downstream repos, the
"Constitution Alignment" section references the wrong principles.

For example, ComplyTime's constitution defines 7 principles
(Single Source of Truth, Simplicity & Isolation, Incremental
Improvement, Readability First, Do Not Reinvent the Wheel,
Composability, Convention Over Configuration) -- none of which
match the headings in the template.

The `schema.yaml` instruction already says "Read the constitution
from `.specify/memory/constitution.md`", but the template itself
contradicts this by hardcoding Unbound Force-specific headings.
Agents following the template produce constitution alignment
sections that reference non-existent principles.

Discovered during complyctl scaffolding: complytime/complyctl#494.

## What Changes

Replace hardcoded constitution principle headings in the proposal
template, design template, and schema instructions with generic
guidance that instructs agents to read the project's constitution
dynamically and generate principle-specific assessments.

## Capabilities

### New Capabilities
- None

### Modified Capabilities
- `templates/proposal.md`: Constitution Alignment section
  replaced with a generic instruction to read the project's
  constitution and assess each principle. No hardcoded
  principle names.
- `templates/design.md`: Remove hardcoded principle name
  references. Use generic "constitution principles" phrasing.
- `schema.yaml`: Remove hardcoded principle names from the
  `design` artifact instruction (line 44). Keep the existing
  `proposal` instruction which already references the
  constitution file.

### Removed Capabilities
- None

## Impact

### Files Modified

**Embedded assets** (deployed to downstream repos):
- `internal/scaffold/assets/openspec/schemas/unbound-force/templates/proposal.md`
- `internal/scaffold/assets/openspec/schemas/unbound-force/templates/design.md`
- `internal/scaffold/assets/openspec/schemas/unbound-force/schema.yaml`

**Live copies** (this repo's working copy):
- `openspec/schemas/unbound-force/templates/proposal.md`
- `openspec/schemas/unbound-force/templates/design.md`
- `openspec/schemas/unbound-force/schema.yaml`

**Tests**:
- `internal/scaffold/scaffold_test.go` -- embedded asset
  match test (`TestEmbeddedAssets_MatchSource`) will pass
  automatically once live and embedded copies are synced.

**NOT modified**:
- Existing proposals under `openspec/changes/` -- they
  already contain filled-in content, not template placeholders
- Archived changes -- preserved as-is
- The `spec.md` and `tasks.md` templates -- no constitution
  references

### Cross-Repo Impact
- Downstream repos using the `unbound-force` OpenSpec schema
  will get the updated template on next `uf init --force`.
  Existing proposals are unaffected (they contain authored
  content, not template text).

## Constitution Alignment

Assessed against the Unbound Force org constitution.

### I. Autonomous Collaboration

**Assessment**: PASS

This change improves artifact quality for downstream repos.
Proposals will produce constitution alignment sections that
reference the correct principles for each project, making
the artifacts more accurate and self-describing.

### II. Composability First

**Assessment**: PASS

The template becomes more composable by not assuming which
constitution principles exist. It works with any constitution
structure -- 4 principles, 7 principles, or any other count.

### III. Observable Quality

**Assessment**: PASS

The schema instruction already directs agents to read the
constitution file. This change aligns the template with that
instruction, removing the contradiction.

### IV. Testability

**Assessment**: PASS

The existing `TestEmbeddedAssets_MatchSource` test verifies
that embedded assets match their live copies. No new test
infrastructure needed.
