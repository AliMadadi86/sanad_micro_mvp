# Sanad Micro MVP - Frozen Decisions

This file freezes the execution decisions for the Micro MVP. Do not change these decisions during implementation unless the project owner explicitly approves it.

## 1. Product Scope

Sanad Micro MVP is a personal online document editor.

The only product path is:

```txt
Register / Login
-> Dashboard
-> Create Document
-> Open Document
-> Edit Text
-> Autosave
```

## 2. In Scope

- Register
- Login
- Current user session
- Personal dashboard
- List documents owned by current user
- Create document
- Open document
- Load document content
- Edit text with Tiptap
- Autosave content
- Display save status

## 3. Out of Scope

- Folder
- Share
- Access / permissions
- Lock
- Realtime
- Comment
- Version History
- File upload
- Public link
- Trash
- Admin panel
- Organization / Company
- Notification
- ActivityLog
- Multi-user collaboration

## 4. Backend Stack

- ASP.NET Core Web API
- C#
- Entity Framework Core
- JWT Authentication
- Swagger / OpenAPI

## 5. Database

- SQL Server

## 6. Frontend Stack

- Next.js
- React
- TypeScript
- Tailwind CSS
- Tiptap
- TanStack Query or a simple API state layer
- React Hook Form
- Zod

## 7. Entities

Only 5 entities exist in the Micro MVP:

```txt
User
Document
DocumentSettings
DocumentContent
DocumentSegment
```

## 8. Entity Relations

```txt
User 1 ---- N Document
Document 1 ---- 1 DocumentSettings
Document 1 ---- 1 DocumentContent
DocumentContent 1 ---- N DocumentSegment
```

For the first implementation, each document may start with one initial segment.

## 9. Auth Decision

Login uses:

```txt
phone_number + password
```

The raw password must never be stored. Store only `password_hash`.

## 10. Content Storage Decision

`Document` does not store editor text.

Text is stored in:

```txt
DocumentSegment.content_json
DocumentSegment.plain_text
```

## 11. Autosave Decision

Autosave is debounced.

Do not save on every keypress.

Use:

```txt
content_hash
version_no
```

for no-op detection and overwrite prevention.

## 12. Start Rule

Do not start from the editor.

Start from:

```txt
Backend Skeleton
-> SQL Server + EF Core
-> Entities
-> Auth
-> Document API
-> Frontend
-> Editor
-> Autosave
```
