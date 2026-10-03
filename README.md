# PureStats plugins

Official plugin sources maintained by PureStats. This repository contains
only MIT-licensed plugin manifests, skills, branding and documentation. The
PureStats backend and its private Git history are not included or licensed here.

## Release status

The packages are currently **pre-launch integration sources**, not a working
production connection or an approved directory listing. Public MCP access at
`https://purestats.io/mcp` is still disabled while protocol, security and client
acceptance tests are completed. ChatGPT also requires its exact publisher
callback and a verified isolated UI origin before activation.

Do not interpret successful package validation or installation as a successful
OAuth connection. Release notes will explicitly announce when production access
and platform-specific acceptance tests have passed.

## Packages

- `chatgpt/`: portable Agent Plugins manifest and Streamable HTTP configuration.
- `claude/`: Claude Code manifest, HTTP configuration and public PKCE client.
- Both packages contain the same four skills: setup, diagnosis, analytics and
  management. No shell hooks, credentials or automatic deployments are bundled.

PureStats is free with unlimited sites and tracked traffic. Technical abuse,
payload and storage safeguards still apply.

## Local package checks

After cloning this public repository, validate the Claude package and marketplace:

```sh
claude plugin validate ./claude
claude plugin validate .
```

For isolated local installation tests, add this directory as a marketplace and
install `purestats@purestats`. This loads the package, but does not enable the
currently disabled production MCP endpoint or grant account access.

## Permissions and authentication

OAuth uses a browser authorization step with PKCE S256. The default request is
limited to `account:read`, `sites:read` and `analytics:read`; users explicitly select
the sites they authorize. Credentials remain in the client's secure OAuth store,
never in this repository, tracking snippets or project source.

Writing settings and accessing sensitive visitor data require additional browser
consent. A human administrator's global privileges are never inherited by an
agent. Site membership is checked on every request. Site deletion, ownership
transfer and account-security changes require a separate, payload-bound human
approval on PureStats; a confirmation in chat is not sufficient.

Existing REST agents can use the documentation at [llms.txt](https://purestats.io/llms.txt)
and the [agent quickstart](https://purestats.io/docs/agents/quickstart).
The HTTP API and MCP share the same permission checks and domain services.

## Releases and checksums

Versioned packages are built from an explicit file allowlist in the private
application repository. ZIP entries have deterministic timestamps, permissions
and ordering. `SHA256SUMS` records the package digests. Public releases will be
published only after their release-specific acceptance checks pass.

No backend commit IDs, private repository metadata, environment files, database
exports or provider credentials are part of the export.

## Support and legal

- Support: [support@purestats.io](mailto:support@purestats.io)
- [Privacy](https://purestats.io/privacy)
- [Terms](https://purestats.io/terms)
- [Security reporting](./SECURITY.md)

Directory submission and approval are separate from publishing these sources.
No official OpenAI or Anthropic directory listing is claimed.
