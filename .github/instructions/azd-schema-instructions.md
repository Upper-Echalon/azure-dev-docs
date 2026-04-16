---
applyTo: "articles/azure-developer-cli/azd-schema.md"
---

# azure.yaml schema documentation conventions

This instruction file defines the structure and conventions for the `azd-schema.md` reference page. Follow these rules when updating the page to ensure incremental, non-destructive edits.

## Source of truth

The JSON schema at `articles/azure-developer-cli/temp-schema.json` (published at <https://aka.ms/azure.yaml.json>) is the single source of truth. All property names, types, descriptions, enum values, and defaults in the documentation must match the schema.

## Update workflow

1. Diff the old schema against the new schema to identify changes (added properties, removed enum values, updated descriptions, new definitions).
1. Apply only the corresponding targeted edits to `azd-schema.md`. Don't regenerate the entire file.
1. Preserve all existing structure, heading hierarchy, and section ordering.

## Page structure (do not reorder)

1. Frontmatter (YAML)
1. H1: title
1. Intro paragraph with template link and schema link
1. `## Sample` — introductory YAML examples
1. `## Top-level properties` — summary table with anchor links
1. One `## {propertyName}` section per top-level property, in the order they appear in the schema's `properties` object: `name`, `resourceGroup`, `metadata`, `infra`, `services`, `resources`, `pipeline`, `hooks`, `requiredVersions`, `state`, `platform`, `workflows`, `cloud`
1. `## docker` — shared Docker definition (referenced from services)
1. `## k8s` — shared AKS definition (referenced from services)
1. Include footer and `## Next steps`

## Section template

Every property section follows this exact pattern:

````markdown
## `{propertyName}`

_(type, required/optional)_ {Description from schema, verbatim or minimally adapted for grammar.}

| Property | Required | Type | Description |
| --- | --- | --- | --- |
| `{childProp}` | Y/N/Conditional | {type} | {Description}. Default: `{value}`. Allowed values: `a`, `b`. |

> [!NOTE]
> {Conditional constraint note, if applicable.}

### {Sub-section for nested objects}

{Same table pattern.}

### {propertyName} samples (if examples exist)

```yaml
{YAML example}
```
````

## Table conventions

- Column order: Property, Required, Type, Description.
- Use `Y`, `N`, or `Conditional` in the Required column.
- Include `Default: {value}.` at the end of the description when a default exists.
- Include `Allowed values: {comma-separated list}.` at the end of the description when an enum exists.
- Use `array of strings` for `{ "type": "array", "items": { "type": "string" } }`.
- Use `object` for complex nested types, with a "See [link](#anchor)" reference.
- Don't add a Type column entry for `$ref` — resolve the reference and document inline or link to the definition section.

## Description conventions

- Use schema `description` text verbatim when possible.
- Adapt only for grammar (for example, sentence fragments become complete sentences).
- Replace "e.g." with "for example" and "i.e." with "that is".
- Don't paraphrase or rewrite descriptions that are already clear.
- Use "can't" not "cannot", contractions per Microsoft style guide.

## Conditional schema (allOf/if/then) conventions

- Document constraints as `> [!NOTE]` blocks below the relevant table.
- For host-type applicability, use the "Host types" matrix table.
- For resource-type applicability, use the "Resource types" table with a link to sub-sections.
- State constraints in plain language: "When `host` is `containerapp`, you must provide either `image` or `project`, but not both."

## YAML examples

- Include one YAML code block per section, showing the property in context.
- Use realistic but generic values (not placeholder `xxx`).
- Keep examples minimal — show the property being documented plus necessary parent structure.
- Use `yaml` as the code fence language.

## What NOT to change during updates

- Frontmatter fields other than `ms.date` (update the date on each edit).
- The intro paragraph and Sample section (unless the schema `title` or `description` changes).
- Section ordering.
- The `## Next steps` section.
- Cross-reference links to other docs (for example, `azd-extensibility.md`).
