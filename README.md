# Sanad Micro MVP

Sanad Micro MVP is a small, real, personal online document editor.

This repository is **only for the Micro MVP**, not the full Sanad MVP.

## Product Goal

Build the smallest usable version of Sanad:

```txt
Register / Login
-> Personal Dashboard
-> Create Document
-> Open Document
-> Edit Text
-> Autosave
-> Refresh and keep content
```

The goal is to validate the core technical path: authentication, document creation, editor loading, segment saving, and autosave.

## In Scope

- User registration
- User login
- Personal dashboard
- Show only the current user's documents
- Create a new document
- Open an existing document
- Edit document text with Tiptap
- Autosave document content
- Show save status in UI: saving / saved / error

## Out of Scope

These features are intentionally excluded from the Micro MVP:

- Folder
- Share
- Access / Permission levels
- Lock
- Realtime collaboration
- Comment
- Version History
- File upload
- Public link
- Trash
- Admin panel
- Organization / Company
- Notification
- ActivityLog

## Final Stack

| Layer | Tool |
|---|---|
| Frontend | Next.js + React + TypeScript |
| UI | Tailwind CSS |
| Editor | Tiptap |
| Backend | ASP.NET Core Web API + C# |
| ORM | Entity Framework Core |
| Database | SQL Server |
| Auth | JWT + password hashing |
| API Docs | Swagger / OpenAPI |
| Local/Dev | Docker optional |

## Entity Slice

Only these 5 entities exist in the Micro MVP:

1. User
2. Document
3. DocumentSettings
4. DocumentContent
5. DocumentSegment

## Repository Structure

```txt
sanad_micro_mvp/
  backend/              ASP.NET Core Web API
  frontend/             Next.js frontend
  docker/               Optional local Docker files
  docs/                 Decisions, tasks, contracts and notes
  README.md
  .gitignore
  .env.example
```

## Execution Order

```txt
B01 - Backend Skeleton
B02 - SQL Server + EF Core
B03 - Create 5 Entities
B04 - Auth
B05 - Document API
B06 - Segment Save API
F01 - Frontend Skeleton
F02 - apiClient
F03 - Auth UI
F04 - Dashboard
F05 - Document Page
F06 - Tiptap Editor
F07 - Autosave UI
I01 - Full Demo Test
```

## First Development Target

The first real milestone is not a beautiful editor.

The first real milestone is:

```txt
User logs in
-> creates a document
-> writes text
-> autosave runs
-> refreshes the page
-> text is still there
```

If this works, the Micro MVP is alive.

## Rule

Do not add full-MVP features to this repository during Micro MVP execution.

If a feature is not required for login -> dashboard -> create document -> editor -> autosave, it is out of scope for now.
