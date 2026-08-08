# Repo Naming Conventions

GitHub doesn't support folders for organizing repositories, so this org uses a naming convention
instead. This doc explains the pattern — both so students can navigate by name, and as a reminder for
whoever's adding new repos.

## Pattern

```
S{semester}-{sequence#}-{ShortName}[-Suffix]
```

- **`S{semester}`** — `S1` or `S2`, whichever semester the repo belongs to.
- **`{sequence#}`** — a two-digit, zero-padded number (`01`, `02`, ... `10`, `11`) showing the order the
  repo is introduced in class that semester. This is a single running count for the semester — it does
  **not** restart per unit.
- **`{ShortName}`** — PascalCase, no spaces, hyphens, or underscores inside it (`TriangleTessellation`,
  not `Triangle_Tessellation` or `triangle-tessellation`). Short enough to scan at a glance.
- **`[-Suffix]`** — optional, only added when it disambiguates something:
  - `-Solution` — a private answer-key repo, if one exists for a task
  - `-Archive` — something retired but kept for reference

## Examples

| Repo name | Meaning |
| --- | --- |
| `S1-01-IntroGithubStarter` | Semester 1, 1st repo introduced, the Intro to GitHub starter |
| `S1-02-TriangleTessellation` | Semester 1, 2nd repo introduced, the tessellation task |
| `S1-02-TriangleTessellation-Solution` | Answer key for the same task, kept private |

## Why zero-padded

Repos sort alphabetically in GitHub's list. Without padding, `S1-10` sorts before `S1-2` once you pass
nine repos in a semester. Padding to two digits (`01`–`99`) avoids that from the start.

## What's exempt

Repos that aren't tied to a specific semester/lesson keep plain, descriptive names instead of a prefix:

- `ReferenceDocs`
- `.github` (the org profile repo)

## Source of truth

The [organization profile README](https://github.com/SSIS-RoboticsCourse-2026-27) keeps the live,
numbered list of every repo — check there before assigning the next sequence number, and add new repos
to that list when they're created.
