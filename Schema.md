# Machine Readable JSON Schema

The schema below represents the v1 schema used by the V20x Evidence Gathering and Analysis tooling.

All objects contain a version string. This value follows the semantic versioning scheme outlined in [Summary#Versioning](./README.md#Versioning)

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "Standardized Scan Result Schema",
  "type": "object",
  "required": ["scanId", "timestamp", "ksiId", "scanType", "status", "results"],
  "properties": {
    "scanId": { "type": "string" },
    "timestamp": { "type": "string", "format": "date-time" },
    "ksiId": { "type": "string" },
    "scanType": { "type": "string" },
    "status": { "type": "string" },
    "results": {
      "type": "object",
      "required": ["summary", "checks"],
      "properties": {
        "summary": {
          "type": "object",
          "required": ["totalChecks", "passed", "failed", "warnings"],
          "properties": {
            "totalChecks": { "type": "integer" },
            "passed": { "type": "integer" },
            "failed": { "type": "integer" },
            "warnings": { "type": "integer" }
          }
        },
        "checks": {
          "type": "array",
          "items": {
            "type": "object",
            "required": ["checkId", "checkType", "name", "status", "severity", "description", "findings"],
            "properties": {
              "checkId": { "type": "string" },
              "checkType": { "type": "string" },
              "name": { "type": "string" },
              "status": { "type": "string" },
              "severity": { "type": "string" },
              "description": { "type": "string" },
              "findings": { "type": "object" }
            }
          }
        }
      }
    }
  }
}
```