# API Contract Draft

This file is a draft contract for the Micro MVP API.

Base path suggestion:

```txt
/api
```

## Health

### GET /health

Response:

```json
{
  "status": "ok"
}
```

## Auth

### POST /auth/register

Request:

```json
{
  "phone_number": "09120000000",
  "first_name": "Ali",
  "last_name": "Madadi",
  "password": "secret"
}
```

Response:

```json
{
  "access_token": "jwt-token",
  "user": {
    "id": "guid",
    "phone_number": "09120000000",
    "first_name": "Ali",
    "last_name": "Madadi"
  }
}
```

### POST /auth/login

Request:

```json
{
  "phone_number": "09120000000",
  "password": "secret"
}
```

Response:

```json
{
  "access_token": "jwt-token",
  "user": {
    "id": "guid",
    "phone_number": "09120000000",
    "first_name": "Ali",
    "last_name": "Madadi"
  }
}
```

### GET /auth/me

Headers:

```txt
Authorization: Bearer <token>
```

Response:

```json
{
  "id": "guid",
  "phone_number": "09120000000",
  "first_name": "Ali",
  "last_name": "Madadi"
}
```

## Documents

### GET /documents

Response:

```json
{
  "items": [
    {
      "id": "guid",
      "title": "Untitled Document",
      "updated_at": "2026-06-02T10:00:00Z"
    }
  ]
}
```

### POST /documents

Request:

```json
{
  "title": "Untitled Document"
}
```

Response:

```json
{
  "id": "guid",
  "title": "Untitled Document"
}
```

### GET /documents/{id}

Response:

```json
{
  "id": "guid",
  "title": "Untitled Document",
  "settings": {
    "page_size": "A4",
    "orientation": "portrait",
    "text_direction": "rtl",
    "default_font_family": "Vazirmatn",
    "default_font_size": 14
  },
  "content": {
    "id": "guid",
    "schema_version": 1
  },
  "segments": [
    {
      "id": "guid",
      "sort_order": 1,
      "content_json": {},
      "plain_text": "",
      "content_hash": "hash",
      "version_no": 1
    }
  ]
}
```

## Segment Save

### PATCH /documents/{documentId}/segments/{segmentId}

Request:

```json
{
  "base_version_no": 1,
  "content_json": {},
  "plain_text": "Hello",
  "content_hash": "new-hash"
}
```

Response:

```json
{
  "segment_id": "guid",
  "version_no": 2,
  "content_hash": "new-hash",
  "saved_at": "2026-06-02T10:00:00Z"
}
```

Conflict response suggestion:

```json
{
  "error": "segment_conflict",
  "message": "Segment has been changed. Please reload the document."
}
```
