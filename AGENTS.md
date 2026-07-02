# AGENTS.md — Relynt Docs

Guidance for AI agents and contributors working on the Relynt documentation site.

## About this project

- Documentation site built on [Mintlify](https://mintlify.com)
- Pages are MDX files with YAML frontmatter
- Configuration lives in `docs.json`
- Audience: **extension builders** — developers authoring and publishing Relynt extensions

## Terminology

| Term | Usage |
|------|-------|
| **extension** | A published package identified by name + semver |
| **bundle** | Directory of manifest files pushed together |
| **manifest** | Single YAML/JSON file with `apiVersion`, `kind`, `metadata`, `spec` |
| **capability** | Typed operation declared in an Extension manifest |
| **content hash** | SHA-256 of canonicalized bundle content |
| **install** | Org-scoped pin of a published extension version |

Use "organization" not "org" in prose (except CLI flag names like `--org`).

## Content boundaries

**Document:**
- Extension platform concepts, manifest authoring, CLI, extension REST/GraphQL APIs
- Validation, CEL, examples from `github.com/getrelynt/manifest` testdata

**Do not document:**
- Internal ops runbooks (deploy, Datadog, EU plan)
- Full platform GraphQL (billing, ingest, enterprise) unless scope expands
- Notion RFC internals — summarize concepts, link to public docs only

## Source material

When updating extension docs, check these repos for accuracy:

| Repo | Content |
|------|---------|
| `github.com/getrelynt/manifest` | Schemas, CEL, validation, `docs/`, `testdata/` |
| `github.com/getrelynt/relynt-cli` | CLI commands, flags, auth setup |
| `github.com/getrelynt/backend` | REST handlers, GraphQL schema (`internal/graph/schema/extension.graphql`) |

## Style

- Second person, active voice
- Sentence case for headings
- Root-relative internal links (`/extensions/quickstart`, no `.mdx` extension)
- All code blocks must have language tags
- No emoji, no marketing filler

## Validation

```bash
mint validate
mint broken-links
```

Run before opening PRs.

## Navigation

New pages must be added to `docs.json` navigation or they won't appear in the sidebar. Match existing tab/group structure:

- **Extensions** — platform guides, manifests, examples
- **CLI** — command reference
- **API reference** — REST (OpenAPI) + GraphQL
