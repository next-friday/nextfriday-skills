# Agent Instructions

Rules for contributing to this repository.

## Style Guidelines

- **No emojis** in any markdown files or code comments
- Use `Yes/No` in tables instead of checkmarks or emoji
- Keep examples concise and focused
- Use `// Bad:` and `// Good:` comments in code examples
- Follow existing file patterns in `skills/nextfriday-best-practices/`

## File Structure

Each skill topic should have:

- Clear heading with brief description
- Code examples showing bad vs good patterns
- Quick reference table at the end

## Code Examples

```tsx
// Bad: description of the problem
<problematic code>

// Good: description of the solution
<correct code>
```

## Naming Conventions

- Skill names: lowercase with hyphens (`nextfriday-best-practices`)
- Reference files: kebab-case (`code-style.md`)
- Keep names under 64 characters

## Adding New Skills

1. Create a new directory under `skills/`
2. Add a `SKILL.md` with proper YAML frontmatter
3. Add reference files at the same level as `SKILL.md`
4. Update `README.md` with the new skill
