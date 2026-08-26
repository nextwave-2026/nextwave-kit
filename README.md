# NextWave Hackathon 2026 preparation kit

This repository is a stack-agnostic preparation kit for the NextWave Hackathon 2026. It contains CI plumbing, two coordination files, a licence policy with a local inventory generator, and document templates. It contains no application scaffold, language choice, dependency manifest, deployment configuration, or domain logic.

## Provenance and ownership

This kit is declared pre-existing intellectual property, authored before the event in its own separate repository. Copy its useful content into the competition entry repository on competition day, and declare that provenance in the entry's first commit and README.

> **Hard warning: this repository must never share git history with the competition entry repository.** If the histories merge, the kit becomes indistinguishable from work done during the event and the ownership clause can swallow it. Copy content into the entry repository instead; the entry's first commit must declare where that pre-existing content came from.

## Competition-day use

1. Copy the needed kit files into a new entry repository without merging or importing this repository's history.
2. Fill in the Makefile bodies as the language and implementation are chosen, but never rename its targets.
3. Use `DECISIONS.md` for append-only decisions and `INTERFACES.md` for the current in-place interface state.
4. Replace the document-template prompts with the entry's actual pitch, README, and Mermaid architecture diagram.
5. Run `make licences` before submission and review the generated inventory for every declared third-party component.

## Makefile contract

The fixed targets are `install`, `lint`, `test`, `build`, `licences`, and `ci`. The first four are green placeholders until competition day; `licences` scans available manifests without network access; `ci` runs all five in order. CI calls the target names directly, so fill in their bodies without renaming the targets.

## Coordination files

`DECISIONS.md` is an append-only log with newest entries at the bottom. It uses the union merge driver so simultaneous appended decisions survive without a conflict. `INTERFACES.md` is edited in place and is deliberately not configured for union merging: retaining both an old and a new interface shape would assert contradictory current states. A conflict in that file is a signal to stop and reconcile the boundary.

## Contents

- `RUNBOOK.md` - shared operating context: schedule, judging, rules, coordination model. Read first.
- `.github/workflows/ci.yml` - separate CI checks for each Makefile stage.
- `DECISIONS.md` - append-only cross-host decision log.
- `INTERFACES.md` - current interface-boundary state.
- `LICENCES.md` and `scripts/licences.py` - policy and offline inventory generation.
- `templates/` - pitch, entry README, and Mermaid architecture templates.
