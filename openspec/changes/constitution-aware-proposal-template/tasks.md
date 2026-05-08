## Tasks

- [ ] 1. Update `openspec/schemas/unbound-force/templates/proposal.md`:
  replace the four hardcoded principle headings (I. Autonomous
  Collaboration, II. Composability First, III. Observable Quality,
  IV. Testability) with a single generic Constitution Alignment
  section containing an instruction comment to read the project's
  `.specify/memory/constitution.md` and assess each principle found
  there.

- [ ] 2. Update `openspec/schemas/unbound-force/templates/design.md`:
  remove the hardcoded reference to "Autonomous Collaboration,
  Composability First, or Observable Quality" and replace with
  generic "constitution principles" phrasing.

- [ ] 3. Update `openspec/schemas/unbound-force/schema.yaml`:
  remove the hardcoded principle names from the `design` artifact
  instruction (line 44). The `proposal` artifact instruction
  already references the constitution file generically and needs
  no change.

- [ ] 4. [P] Sync embedded scaffold copies: copy the updated
  live files to their embedded asset counterparts under
  `internal/scaffold/assets/openspec/schemas/unbound-force/`.

- [ ] 5. Run `go test ./internal/scaffold/ -run TestEmbeddedAssets`
  to verify embedded assets match their live copies.
