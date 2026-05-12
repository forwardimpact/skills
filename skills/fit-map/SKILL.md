---
name: fit-map
description: >
  Define what good engineering means so roles have clear, defensible
  expectations. Use when managers disagree on what a level requires and
  you need a written standard, when defining or updating skills,
  capabilities, behaviours, disciplines, tracks, levels, and questions,
  or when pushing people rosters, syncing GetDX snapshots, ingesting
  GitHub artifacts, and verifying the activity database.
license: Apache-2.0
metadata:
  version: "0.1.0"
  author: forwardimpact
---

# Map Product

A public data model for consumption by AI agents and engineers. Map is the
foundation of all Forward Impact products — it defines how engineering
competencies, career progression, and agent capabilities are structured in a
machine-readable format. Map ships two layers: a **standard layer** (YAML files
validated against JSON Schema and RDF/SHACL) and an **activity layer** (a
Supabase project with `organization_people`, GitHub artifacts, GetDX snapshots,
and marker evidence).

Making the data model well understood is a first-class goal. It is published in
structured formats (JSON Schema, RDF/SHACL) so that AI agents can reliably
interpret and work with agent-aligned engineering standard data.

## When to Use

**Defining or updating your engineering standard:**

- Defining or tailoring engineering expectations for your organization
- Adding or modifying skills, behaviours, disciplines, tracks, or levels
- Adding interview questions to skill or behaviour files
- Working with JSON Schema or RDF/SHACL definitions

**Validating and inspecting standard data:**

- Validating standard data integrity after changes — `npx fit-map validate`
- Checking data summary (skill counts, entity counts) — `npx fit-map validate`
- Generating browser index files — `npx fit-map generate-index`
- Exporting base entities to HTML microdata — `npx fit-map export`

**Activity-layer operations:**

- Starting and checking the local Supabase stack — `npx fit-map activity start`
- Validating a people roster against the standard — `npx fit-map people validate <file>`
- Pushing a people roster into the activity database — `npx fit-map people push <file>`
- Syncing GetDX snapshots — `npx fit-map getdx sync`
- Reprocessing the raw bucket — `npx fit-map activity transform`
- Verifying the activity database is populated — `npx fit-map activity verify`

---

## How It Works

### Data Loading

Map loads YAML files from structured directories (`disciplines/`, `tracks/`,
`capabilities/`, `behaviours/`, `levels.yaml`, etc.). Skills are extracted from
capability files during loading — they live inside capabilities rather than as
standalone files. The result is a unified data object containing all entities
with their cross-references resolved by ID.

### Validation Pipeline

Validation runs in two phases:

1. **Schema validation** — each YAML file is checked against its corresponding
   JSON Schema (e.g. capability files against `capability.schema.json`). This
   catches structural issues like missing required fields or wrong types.
2. **Referential integrity** — after schema passes, cross-references are
   verified: skill IDs referenced by disciplines must exist in capabilities,
   behaviour IDs in tracks must exist, track IDs in discipline `validTracks`
   must exist, driver `contributingSkills` and `contributingBehaviours` must
   point to valid entities, and level references (`minLevel`) must resolve.

### Index Generation

The index generator creates `_index.yaml` files in each entity directory,
listing all valid file IDs. These indexes enable browser-based discovery without
filesystem access — the web app loads them to know which entities are available.

---

## CLI Reference

See [`references/cli.md`](references/cli.md) for full command listings.

### Edge functions (hosted-only)

Four edge functions ship in the bundled Supabase project and deploy with
`supabase functions deploy`:

| Function         | Trigger                                    | Responsibility                                                                        |
| ---------------- | ------------------------------------------ | ------------------------------------------------------------------------------------- |
| `github-webhook` | POST from a configured GitHub webhook      | Store raw payload + upsert `github_events`, `github_artifacts` with email resolution  |
| `people-upload`  | POST with a CSV/YAML body                  | Store raw upload + upsert `organization_people` (equivalent to `fit-map people push`) |
| `getdx-sync`     | Scheduled POST (cron, GitHub Actions, etc) | Fetch + store + transform GetDX (equivalent to `fit-map getdx sync`)                  |
| `transform`      | On-demand POST                             | Reprocess the `raw` bucket end-to-end (equivalent to `fit-map activity transform`)    |

Every edge function returns a JSON response with per-target counts and errors.
Full walk-through in the
[engineering leaders getting-started guide](https://www.forwardimpact.team/docs/getting-started/leaders/index.md#activity-ingest-github-activity).

---

## Data Structure

```
data/pathway/
├── standard.yaml         # Standard metadata, entity definitions
├── levels.yaml            # Career levels (J040, J060, etc.)
├── stages.yaml            # Lifecycle stages (plan, code, review, etc.)
├── drivers.yaml           # Organizational outcomes
├── disciplines/           # Engineering specialties (software_engineering, etc.)
├── tracks/                # Work contexts (platform, forward_deployed, etc.)
├── behaviours/            # Approach to work (outcome_ownership, etc.)
├── capabilities/          # Skills grouped by area (delivery, scale, etc.)
├── repository/            # Repository configuration (vscode-settings, devcontainer, etc.)
└── questions/             # Interview questions
    ├── skills/            # Per-skill question sets
    └── behaviours/        # Per-behaviour question sets
```

Entity files use **co-located content** — `human:` and `agent:` sections in the
same YAML file. All entities have an `id` field used for cross-references.

---

## Schema Definitions and Common Tasks

See [`references/tasks.md`](references/tasks.md) for schema locations and
authoring tasks.

## Verification

Always run validation after changes:

```sh
npx fit-map validate
```

## Documentation

- [Map Overview](https://www.forwardimpact.team/map/index.md) — Product
  overview, audience model, and key concepts
- [Getting Started: Map for Leaders](https://www.forwardimpact.team/docs/getting-started/leaders/map/index.md)
  — From zero to a validated engineering standard
- [Authoring Agent-Aligned Engineering Standards](https://www.forwardimpact.team/docs/products/authoring-standards/index.md)
  — End-to-end guide to defining your engineering standard in YAML
- [Validate and Update the Standard](https://www.forwardimpact.team/docs/products/authoring-standards/update-standard/index.md)
  — Run validation, interpret errors, and update safely
- [Define a New Role](https://www.forwardimpact.team/docs/products/authoring-standards/define-role/index.md)
  — Add a discipline, track, or capability to the standard
- [YAML Schema Reference](https://www.forwardimpact.team/docs/reference/yaml-schema/index.md)
  — File format reference for every entity type
- [Provision Engineer Auth Users](https://www.forwardimpact.team/docs/products/provisioning-engineers/index.md)
  — Reconcile auth.users against the roster so identity-derived RLS works
