# Repository Rules

## 1. Branches

Use this simple branch strategy:

```txt
main                 stable branch
feature/B01-*        backend task branches
feature/F01-*        frontend task branches
fix/*                bug fixes
```

## 2. Commit Message Style

Use short, clear messages:

```txt
chore: initialize repository
feat(auth): add login endpoint
feat(documents): create document endpoint
fix(autosave): prevent duplicate saves
```

## 3. Pull Request Rule

Every PR must include:

- What changed
- How to test it
- Related task ID

Example:

```txt
Task: B01
What changed: Added ASP.NET Core backend skeleton and health endpoint.
How to test: Run backend and open /health.
```

## 4. Scope Rule

Do not add full-MVP features into this Micro MVP repository.

Forbidden during Micro MVP:

- Folder
- Share
- Access
- Lock
- Realtime
- Comment
- Version History
- File upload

## 5. Done Rule

A task is not done when code is written.

A task is done when:

- It runs
- It can be tested
- It matches the task output
- It does not break the Micro MVP scope
