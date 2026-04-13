# Plan: Hermes Documentation Extraction & Agent Guidance

## Goal
Extract specific documentation from the remote Hermes Agent repository for local reference and update project documentation to clarify agent roles within the OhMyOpenCode pipeline.

## Scope
- **IN**:
    - Remote path: `https://github.com/NousResearch/hermes-agent.git` -> `website/docs/**`
    - Local output: `docs/reference/hermes-doc-pack.md`
    - Guidance: Update `README.md` with a section on Agent Roles (Prometheus vs. Sisyphus/Build).
- **OUT**:
    - Packing any other parts of the remote repository.
    - Modifying existing documentation in the remote repository.

## Technical Approach
- Use `npx repomix@latest` with the `--remote` and `--include` flags to isolate the documentation directory.
- Update the local `README.md` to resolve user confusion regarding the distinction between the Planner (Prometheus) and the Implementer (Sisyphus/Build).

## Implementation Tasks

### Phase 1: Documentation Extraction
1. **Execute Repomix Extraction**:
    - Command: `npx repomix@latest --remote https://github.com/NousResearch/hermes-agent.git --include "website/docs/**" --output docs/reference/hermes-doc-pack.md`
    - QA Scenario: Verify that the command completes without errors and the output file is created.
2. **Verify Extraction Quality**:
    - Action: Read the first 100 lines of `docs/reference/hermes-doc-pack.md`.
    - QA Scenario: Ensure the file starts with the expected Repomix header and contains content from the `website/docs` directory.

### Phase 2: Agent Guidance Documentation
3. **Update README with Agent Roles**:
    - Action: Add a section titled `## Agent Roles` to `README.md`.
    - Content: Explain that **Prometheus** is the Strategic Planner (creates work plans, does not write code) and **Sisyphus/Build agents** are the Implementers (execute plans, write code). Mention that running `/start-work` triggers the transition from planning to execution.
    - QA Scenario: Verify the section is clearly visible and accurately describes the roles.


## Final Verification Wave
- [x] Verify `docs/reference/hermes-doc-pack.md` exists and contains content from `website/docs/**`.
- [x] Verify `README.md` contains the "Agent Roles" section.
- [x] Explicit User "Okay" to mark work as complete.
