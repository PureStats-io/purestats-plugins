---
name: purestats-setup
description: Set up a PureStats site and its existing tracker in an authorized HTML, React, Next.js or Laravel project, then verify installation without polluting production analytics.
---

# Set up PureStats

1. Read https://purestats.io/llms.txt and the linked installation guidance.
   Use the connected tools to read `account_capabilities` and `sites_list`.
   Do not automate passwords or browser sessions. If MCP is unavailable, report
   that state rather than pretending the site was created or tracking works.
2. Reuse the intended existing site. Only call `sites_create` when a new site is
   explicitly requested and `sites:create` has been granted. Keep the same
   idempotency key for retries of the same unchanged request.
3. Call `sites_installation` with the site's ID and the actual framework. Use
   the returned `pf.min.js` snippet, CSP and module guidance; do not fork the
   tracker or include management credentials in browser code.
4. Make a scoped project edit only when the user has authorized project writes.
   For a first-party proxy, preserve signed visitor-IP forwarding, module paths,
   cache behavior and retry semantics from the returned instructions.
   Deployment still requires the user's project-specific authorization.
5. Start `sites_installation_tests_start`, load the project in a real browser
   using its returned test instructions, poll the status and stop the test.
   Test sessions must remain outside production visitors, conversions and rollups.
6. Report domain proof, snippet detection, script loading, browser test and
   real stored hits separately. A verified domain or an HTTP 2xx alone is not
   evidence of a stored tracking event.

Use only granted sites. A missing scope or browser handoff is a required user
action, not permission to try a different account, transport or site ID.
