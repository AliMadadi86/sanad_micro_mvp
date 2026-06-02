# Sanad Micro MVP - Task List

Use these IDs in Gitea issues, GitHub issues, Trello, ClickUp, or Jira.

A task is done only when its output is testable.

## Backend Tasks

### B01 - Backend Skeleton

Goal: Create a clean ASP.NET Core Web API project.

Output:

- Backend project runs locally
- Swagger opens
- `GET /health` returns `{ "status": "ok" }`
- README/run notes exist for backend

Done:

- Fresh clone can run backend with documented commands
- No database dependency yet

### B02 - SQL Server + EF Core

Goal: Connect backend to SQL Server with EF Core.

Output:

- DbContext exists
- Connection string is read from config
- First migration works
- Database can be created locally

Done:

- Migration can be applied without manual database edits

### B03 - Create 5 Entities

Goal: Implement the Micro MVP entity slice.

Entities:

- User
- Document
- DocumentSettings
- DocumentContent
- DocumentSegment

Done:

- Tables are created by migration
- Relations are correct
- No full-MVP entities are added

### B04 - Auth

Goal: Register and login users.

Endpoints:

- `POST /auth/register`
- `POST /auth/login`
- `GET /auth/me`

Done:

- Password is hashed
- JWT is returned on login
- Protected endpoints reject unauthenticated requests

### B05 - Document API

Goal: Create and open documents.

Endpoints:

- `GET /documents`
- `POST /documents`
- `GET /documents/{id}`
- `PATCH /documents/{id}` for title rename

Done:

- User sees only own documents
- Creating a document also creates settings, content, and an initial segment

### B06 - Segment Save API

Goal: Save editor content to DocumentSegment.

Endpoint:

- `PATCH /documents/{documentId}/segments/{segmentId}`

Done:

- Validates ownership
- Checks base version
- Updates content_json, plain_text, content_hash, version_no
- Does not update when hash is unchanged

## Frontend Tasks

### F01 - Frontend Skeleton

Goal: Create Next.js frontend project.

Routes:

- `/login`
- `/register`
- `/dashboard`
- `/documents/[id]`

Done:

- Routes open
- Base layout exists
- RTL support exists

### F02 - apiClient

Goal: Create a central API client.

Done:

- Reads base URL from env
- Adds JWT token when available
- Handles 401 globally

### F03 - Auth UI

Goal: Build register/login screens.

Done:

- Register works
- Login works
- Token is saved
- Logout clears session
- Protected routes redirect to login

### F04 - Dashboard

Goal: Show personal documents.

Done:

- Loading, empty, error, success states exist
- User can create a new document
- User can open a document

### F05 - Document Page

Goal: Load document data and show editor shell.

Done:

- Document metadata loads
- Segment content loads
- Error state appears if document does not belong to user

### F06 - Tiptap Editor

Goal: Edit document text with Tiptap.

Done:

- Initial content loads from segment
- User can type and edit text
- Editor supports RTL Persian text

### F07 - Autosave UI

Goal: Implement debounced autosave.

Done:

- Shows saving / saved / error
- Does not save on every keypress
- Refresh keeps the latest saved text

## Integration Tasks

### I01 - Register/Login Flow

A user can register, login, and reach dashboard.

### I02 - Create Document Flow

A logged-in user can create a document and see it in dashboard.

### I03 - Open Document Flow

A logged-in user can open own document and load editor content.

### I04 - Edit + Autosave Flow

A user can type, wait for autosave, refresh page, and see saved content.

### I05 - Security Smoke Test

User A must not see or edit User B's documents.
