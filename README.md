# Next Friday Agent Skills

Agent skills for Next Friday development workflows. Follows the [Agent Skills open standard](https://github.com/anthropics/skills).

## Installation

```bash
# Install essentials (recommended)
npx skills add next-friday/nextfriday-skills --skill nextfriday-best-practices

# Or install specific skills
npx skills add next-friday/nextfriday-skills --skill nextfriday-naming
npx skills add next-friday/nextfriday-skills --skill nextfriday-code-style
npx skills add next-friday/nextfriday-skills --skill nextfriday-react

# Or install everything
npx skills add next-friday/nextfriday-skills
```

## Essential Skills

Background skills that are auto-applied when relevant.

| Skill | Description | Rules |
| ----- | ----------- | ----- |
| `nextfriday-best-practices` | Complete Next Friday coding standards | 41 |

## Focused Skills

Install only what you need.

| Skill | Description | Rules |
| ----- | ----------- | ----- |
| `nextfriday-naming` | Variable, constant, and file naming conventions | 9 |
| `nextfriday-code-style` | Code formatting, structure, and readability | 13 |
| `nextfriday-imports` | Import statements and module resolution | 3 |
| `nextfriday-types` | TypeScript type patterns and annotations | 6 |
| `nextfriday-react` | React/JSX component patterns | 8 |
| `nextfriday-nextjs` | Next.js specific rules | 2 |

## Skill Details

### nextfriday-best-practices

The complete guide covering all 41 rules across 7 topics:

- [variable-naming.md](skills/nextfriday-best-practices/variable-naming.md) - Boolean prefixes, constants, meaningful names
- [file-naming.md](skills/nextfriday-best-practices/file-naming.md) - kebab-case, PascalCase, SNAKE_CASE conventions
- [code-style.md](skills/nextfriday-best-practices/code-style.md) - Guard clauses, async/await, formatting
- [imports.md](skills/nextfriday-best-practices/imports.md) - Absolute imports, type imports
- [types.md](skills/nextfriday-best-practices/types.md) - Props interfaces, return types
- [react-jsx.md](skills/nextfriday-best-practices/react-jsx.md) - Suspense, props destructuring
- [nextjs.md](skills/nextfriday-best-practices/nextjs.md) - Environment variables

## Related

- [eslint-plugin-nextfriday](https://github.com/next-friday/eslint-plugin-nextfriday) - ESLint plugin with the same rules
