# AUDITOR — Functional Specification

## 1. Repository inventory

For every accessible repository, collect:

- `full_name`
- `name`
- `description`
- `visibility`
- `archived`
- `default_branch`
- `created_at`
- `updated_at`
- `pushed_at` when available
- `size`
- topics
- fork status
- upstream/original repository when available

## 2. Activity analysis

Calculate activity inside the rolling 24-month window and expose at least:

- commits in 90 days;
- commits in 12 months;
- commits in 24 months;
- months with at least one commit;
- last meaningful commit date;
- latest commit message;
- contributor count when available;
- open/closed PR activity when available.

Activity must be classified as:

```text
ACTIVE
MAINTAINED
LOW_ACTIVITY
STALE
DORMANT
```

Suggested interpretation:

- ACTIVE: meaningful activity in the last 90 days;
- MAINTAINED: meaningful activity in 3–12 months;
- LOW_ACTIVITY: activity in 12–24 months but sparse;
- STALE: no activity for 24–36 months;
- DORMANT: no activity for more than 36 months.

## 3. Content analysis

Inspect the default branch for representative project files:

- README;
- package manifests;
- `pyproject.toml` / `requirements.txt`;
- `package.json`;
- `composer.json`;
- `go.mod`;
- `Cargo.toml`;
- `pom.xml` / `build.gradle`;
- Docker files;
- CI workflows;
- source directories;
- docs directories.

Infer:

- language;
- framework;
- application type;
- deployment model;
- database;
- authentication;
- testing;
- CI/CD;
- documentation maturity;
- project maturity.

## 4. Duplication analysis

Group repositories that appear to belong to the same project family using:

- name similarity;
- descriptions;
- technology overlap;
- README references;
- directory structure;
- dependency fingerprints;
- Git history similarity where practical.

Examples of a family:

```text
calendrierDivin
calendrierDivin-update
CalendierDivin-v3
calendrier-divin-editor
```

The auditor should identify a likely canonical repository but must not automatically choose one when evidence is ambiguous.

## 5. External-source / fork analysis

Detect repositories that appear to be:

- forks;
- upstream clones;
- vendor source copies;
- course exercises;
- starter templates;
- generated prototypes;
- imported resources.

Such repositories receive a portfolio penalty unless there is clear original value.

## 6. Portfolio relevance

Evaluate alignment with the current strategic domains:

```text
HashCode
E-Flex
Cybersecurity
AI / Applied AI
Cloud / DevOps
Web Engineering
Education / Academy
Developer Tools
Open Source
Research
```

## 7. Recommendation engine

Output a deterministic recommendation plus explanation.

Example:

```json
{
  "repository": "digitaleflex/example",
  "activity": "DORMANT",
  "portfolio_score": 18,
  "recommendation": "ARCHIVE",
  "reasons": [
    "No meaningful activity in 36 months",
    "Starter/template repository",
    "No strategic dependency detected"
  ]
}
```

## 8. Human review queue

The system must generate three priority queues:

### Immediate review
High-confidence cleanup candidates.

### Strategic review
Potentially valuable but ambiguous projects.

### Protect
Repositories that must not be touched without dependency/deployment review.

Examples likely to receive `Protect` status include active production systems, infrastructure repositories, client projects, and core HashCode products.

## 9. Non-destructive execution

Version 1 is analysis-only.

No delete/archive/rename/write operation against external repositories is part of the auditor execution path.
