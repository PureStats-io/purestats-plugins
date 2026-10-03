---
name: purestats-manage
description: Manage explicitly authorized PureStats goals, funnels, segments, dashboards, settings, reports and integrations with idempotent writes and payload-bound human approval for dangerous changes.
---

# Manage PureStats

Read `account_capabilities` and the current resource before proposing a change.
Use only the exact selected site and supported tools. An administrator's global
permissions are not available through an agent grant.

Confirm the intended mutation and preserve unrelated settings. Every mutating
operation uses an idempotency key of at least eight characters. Reuse that key
only for retries of the identical operation, site and payload; changing the
payload requires a new key. Verify the saved result through a read operation.

If an operation returns `interactive_required`, open the supplied PureStats
handoff for the user. External Google/Bing authorization must run in that
browser flow; never request, reveal or reuse stored provider secrets.

Deletion, ownership transfer, privacy-sensitive and account-security changes
require the service's payload-bound human approval. Present its preview and
approval URL; wait for the human owner to approve there, then submit the unchanged
payload with the supplied approval ID and original idempotency key. A chat
confirmation is not sufficient. A changed or expired approval must be recreated.
Machine accounts must be claimed by a human before these actions can proceed.

Never execute project deployments, shell hooks, bulk deletions or account
changes merely because a plugin has been installed. Stop on denied scopes,
revoked membership or validation errors and explain the specific user action
required to continue.
