# Machine Readable JSON Schema

The schema below represents the v1 schema used by the V20x Evidence Gathering and Analysis tooling.

All objects contain a version string. This value follows the semantic versioning scheme outlined in [Summary#Versioning](./README.md#Versioning)

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "Assessment",
  "type": "object",
  "properties": {
    "version": { "type": "string" },
    "id": { "type": "string" },
    "name": { "type": "string" },
    "createdBy": { "type": "string" },
    "createdAt": { "type": "string", "format": "date-time" },
    "allowedUsers": {
      "type": "array",
      "items": {
        "type": "object",
        "properties": {
          "userId": { "type": "string" },
          "canEdit": { "type": "boolean" },
          "canDelete": { "type": "boolean" },
          "canTriggerRescan": { "type": "boolean" }
        },
        "required": ["userId", "canEdit", "canDelete", "canTriggerRescan"]
      }
    },
    "description": { "type": "string" },
    "status": {
      "type": "string",
      "enum": ["not-started", "in-progress", "completed", "under-review", "blocked"]
    },
    "type": {
      "type": "string",
      "enum": ["full", "20x-initial", "20x-automatic"]
    },
    "parentAssessmentId": { "type": "string" },
    "lastUpdatedAt": { "type": "string", "format": "date-time" },
    "dueDate": { "type": "string", "format": "date-time" },
    "assignedTo": { "type": "string" },
    "category": {
      "type": "string",
      "enum": ["fedramp", "commercial"]
    },
    "deletionRecord": {
      "type": "object",
      "properties": {
        "version": { "type": "string" },
        "deletedAt": { "type": "string", "format": "date-time" },
        "deletedBy": { "type": "string" },
        "reason": { "type": "string" }
      },
      "required": ["version", "deletedAt", "deletedBy"]
    },
    "ksiRecords": {
      "type": "object",
      "additionalProperties": {
        "type": "object",
        "properties": {
          "version": { "type": "string" },
          "attestations": {
            "type": "array",
            "items": {
              "type": "object",
              "properties": {
                "version": { "type": "string" },
                "attestedAt": { "type": "string", "format": "date-time" },
                "attestedBy": { "type": "string" },
                "revokedAt": { "type": "string", "format": "date-time" },
                "revokedBy": { "type": "string" }
              },
              "required": ["version", "attestedAt", "attestedBy"]
            }
          },
          "documentUploads": {
            "type": "array",
            "items": {
              "type": "object",
              "properties": {
                "version": { "type": "string" },
                "uploadedAt": { "type": "string", "format": "date-time" },
                "uploadedBy": { "type": "string" },
                "document": { "type": "string" }
              },
              "required": ["version", "uploadedAt", "uploadedBy", "document"]
            }
          },
          "automatedScans": {
            "type": "array",
            "items": {
              "type": "object",
              "properties": {
                "version": { "type": "string" },
                "scannedAt": { "type": "string", "format": "date-time" },
                "scanResult": {
                  "type": "string",
                  "enum": ["pass", "fail", "inconclusive", "error"]
                },
                "scanDetails": { "type": "string" },
                "requestedBy": { "type": "string" }
              },
              "required": ["version", "scannedAt", "scanResult"]
            }
          },
          "lastUpdatedAt": { "type": "string", "format": "date-time" }
        },
        "required": ["version"]
      }
    }
  },
  "required": [
    "version", "id", "name", "createdBy", "createdAt", "description",
    "status", "type", "lastUpdatedAt", "category"
  ]
}
```