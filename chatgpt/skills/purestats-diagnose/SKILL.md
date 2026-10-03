---
name: purestats-diagnose
description: Diagnose missing or inconsistent PureStats tracking, proxy setup, timezone, traffic filters and OAuth permissions using authorized installation and analytics tools.
---

# Diagnose PureStats

Establish the site ID, timezone, date range and traffic mode before comparing
results. Read `account_capabilities`, `sites_settings_get` and
`sites_tracking_test_overview` where their scopes are available.

Separate domain ownership, accepted alias hosts, installed script, test-session
status and real stored events. An alias's verification timestamp is not proof
that tracking has been rejected. Compare timezone-aligned buckets and distinguish
unique visitors from visits, sessions, pageviews and source attribution.

For browser/proxy problems, check the installation response, CSP, consent/DNT,
path exclusions, bot mode, module loading and signed client-IP forwarding.
A proxy may dequeue only a valid JSON response with a known `ingest_status`.
Never expose proxy signing secrets or infer a visitor's IP from the server IP.

Use the installation test workflow for reproductions. Do not create fake
production visits or read visitor profiles without the sensitive-data scope.
Sanitize logs and screenshots before sharing them.

For OAuth problems, distinguish expired tokens, revoked grants, lost site
membership, insufficient scopes and a disabled endpoint. Reauthorization belongs
in the browser; do not automate 2FA or broaden a grant without consent. Retrying
an unchanged write keeps its original idempotency key. Stop repeated retries on
authorization, validation or payload-conflict errors; honor `Retry-After` for
temporary rate limiting.
