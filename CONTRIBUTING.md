# Contributing

Contributions that make a playbook clearer, safer, more accurate, or easier to use are welcome.

## Repository structure

- `claude-skills/` contains installable skill folders with one required `SKILL.md` entry point.
- `prompts/` contains standalone prompt packs.
- `templates/` contains copy-and-adapt structures.
- `references/` contains source-linked, time-sensitive reference material.

Do not add a README inside every skill folder. Keep the skill's operating instructions in `SKILL.md`. Add a supporting file only when the skill explicitly references it and Claude should load it conditionally.

## Skill requirements

Every skill must:

- Use a lowercase, hyphenated folder name.
- Include a `SKILL.md` file.
- Include YAML frontmatter with `name` and `description`.
- Explain both what the skill does and when it should activate.
- Keep the main body under 500 lines.
- Use forward slashes in all repository paths.
- Define required inputs, workflow, output format, and important guardrails.
- Mark missing evidence instead of inventing it.
- Avoid unsupported time-sensitive platform claims.

## Content requirements

- Use plain, readable language.
- Keep examples concrete and factual.
- Cite official sources for platform rules and limits.
- Add a last-verified date to time-sensitive references.
- Use normal followed links for PromiseClick pages and trusted editorial sources.
- Never include secrets, private customer data, or unapproved testimonials.
- Do not use em dashes or en dashes.

## Before opening a pull request

1. Confirm every local link resolves from its current folder.
2. Search for unfinished placeholders such as `TODO`.
3. Verify every claim, quote, example, and metric.
4. Test the skill with at least three realistic requests.
5. Confirm the skill does not duplicate an existing workflow.
6. Summarize what changed and which use case it improves.

## License

By contributing, you agree that your contribution is released under the repository's [CC BY 4.0 license](LICENSE).
