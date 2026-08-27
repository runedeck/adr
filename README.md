# runeADR

The decision-record format of the runedeck ecosystem. One markdown file per decision,
structured frontmatter for machines, a fixed body shape for humans, and a schema that
validates both.

## Lineage

runeADR extends [Structured MADR](https://github.com/modeled-information-format/structured-madr) with
accountability and provenance fields. The format documentation lives at [smadr.dev](https://smadr.dev).

The bare field names below are canonical. The compliant long form carries the
`x-rune-` prefix (`x-rune-accountable`), so a strict Structured MADR validator
accepts a runeADR record.

Upstream ships more than the specification: a JSON Schema, record templates, and a
GitHub Action validator for CI. The upstream [SPECIFICATION](https://github.com/modeled-information-format/structured-madr/blob/main/SPECIFICATION.md)
also defines risk-assessment and audit sections, which runeADR treats as optional.
runeADR carries its own JSON Schema for the field set below.

## Frontmatter

| Field | Type | Purpose |
| --- | --- | --- |
| `title` | string | Short noun phrase naming the decision |
| `description` | string | The decision in one sentence |
| `type` | string | Always `adr` |
| `category` | string | `architecture`, `process`, or `security` |
| `tags` | list | Free-form topics |
| `status` | string | `proposed`, `accepted`, `deprecated`, or `superseded` |
| `created`, `updated` | date | Lifecycle dates |
| `author` | string | The record's author |
| `project` | string | The owning project |
| `related` | list | Neighbor records, by name |
| `upstream` | list | Sources the decision follows. An empty list is a statement |
| `responsible` | list | RACI: who does the work |
| `accountable` | list | RACI: who approves the decision |
| `consulted` | list | RACI: whose input is sought |
| `informed` | list | RACI: who hears the outcome |

Frontmatter stays flat: strings and lists of strings. A value that contains a colon
is quoted.

## Body

```text
# <Title>
## Context and Problem Statement   <- the forces and the question
## Decision Drivers                <- optional
## Considered Options              <- a numbered list
## Decision Outcome                <- the choice and its rule
### Consequences                   <- [+] and [-] bullets
## More Information                <- optional: amendments, references
```

## Files

- `template.md`: the record template. Instantiate with
  `envsubst < template.md > "CORE-0001 Title.md"`. The `%%` comments describe each
  variable.
- `adr.mdschema`: the structural validation schema. Copy it into your decisions
  directory as `.mdschema`.
- `runeadr.schema.json`: the JSON Schema, for CI that validates frontmatter as
  data. Bare fields are canonical, and `x-rune-` prefixed fields pass for
  compliance with strict Structured MADR validators.

## Naming

Records live in `docs/decisions/` and use spaced names:
`CORE-0001 Markdown as System Language.md`. The identifier is identity: one number,
one decision, one series.

## License

EUPL-1.2. See `LICENSE`.
