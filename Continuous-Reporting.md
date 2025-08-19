# Continuous Reporting

One of the core tenants of the FedRAMP20x project is continuous reporting of KSI compliance.

V20x supports continuous reporting in one of two ways:
1. Scheduled rescans: For any KSI that can be automatically checked the tool can be configured to periodically scan, and report results.
1. Scheduled re-assesment: For systems undergoing active development, or significant changes, V20x can be configured to periodically generate an entirely new assesment. Each assesment is linked to the previous assesment generated. This behavior allows for both automatic, and manual evidence collection on a client-configurable schedule.

**Note:** By default V20x operates in 'Scheduled Rescan' mode with a weekly scan cadence.

Automated scans can also be manually triggered by a user with the correct permissions.

## History

New assesments, and scans, are non-destructive. This allows V20x to provide a history of compliance, KSI pass rates, and auditing.
