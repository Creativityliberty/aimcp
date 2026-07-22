# Nümtema MCP Foundry v1.3.0

Nümtema MCP Foundry transforms OpenAPI 3.x services into governed MCP and ChatGPT applications with OAuth 2.1, approval boundaries, durable dispatch, provider adapters, signed receipts, a local-first Studio, and deployable Coolify/VPS packages.

```text
OpenAPI
→ Source Inspector
→ Capability Map
→ governed Tool Contracts
→ OAuth / Policy / Approval
→ MCP Runtime
→ Foundry Studio
→ Coolify deployment package
```

## Current release

- Version: `1.3.0`
- Node.js: `22+`
- Runtime dependencies: `0`
- Tests: `145`
- Suites: `59`
- GitHub governance: `AGENTS.md`, contribution/security rules, CI templates
- Deployment: exact Coolify manual configuration runbook

## Install

Download the npm tarball from the project release bundle, then:

```bash
npm install --global ./numtema-mcp-foundry-1.3.0.tgz
foundry doctor
```

## Create a Studio project

```bash
foundry studio init ./my-foundry --name "My MCP"
foundry studio serve ./my-foundry
```

Build a deployable package:

```bash
foundry studio build ./my-foundry
```

The generated deployment package is written to:

```text
my-foundry/deploy/package
```

## Documentation

- Agent operating contract: [`AGENTS.md`](AGENTS.md)
- Coolify configuration: [`docs/deployment/COOLIFY_CONFIGURATION.md`](docs/deployment/COOLIFY_CONFIGURATION.md)
- GitHub publishing: [`docs/deployment/GITHUB_PUBLISHING.md`](docs/deployment/GITHUB_PUBLISHING.md)
- Contributing: [`CONTRIBUTING.md`](CONTRIBUTING.md)
- Security: [`SECURITY.md`](SECURITY.md)

## Security invariants

- no provider secret, OAuth token, password, refresh token, private PEM, or vault locator in artifacts or commits;
- no provider network call before policy, credential, approval, budget, and Ledger gates pass;
- risk and approval requirements may not be silently weakened;
- private keys are generated at first run and kept only in persistent runtime storage;
- one active writer per local durable Ledger volume.

## Temporary repository name

This repository is currently published as `Creativityliberty/aimcp`. It can be renamed to `numtema-mcp-foundry` from GitHub repository settings without changing the project contents.
