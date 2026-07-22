# Publishing to GitHub

Current delivery repository: `Creativityliberty/aimcp`.

The repository may be renamed to `numtema-mcp-foundry` from GitHub **Settings → General → Repository name**. GitHub redirects the old URL after a rename.

## Publish the complete local source tree

Download and extract the v1.3 ZIP, then run from the project root:

```bash
./scripts/publish-github.sh Creativityliberty/aimcp
```

The script:

1. runs the secret audit;
2. runs TypeScript type checking;
3. runs the complete test suite;
4. creates or updates the `origin` remote;
5. pushes branch `main`.

Manual equivalent:

```bash
./scripts/audit-secrets.sh
npm run typecheck
npm test

git branch -M main
git remote remove origin 2>/dev/null || true
git remote add origin https://github.com/Creativityliberty/aimcp.git
git push --set-upstream origin main
```

## Recommended GitHub settings

- Default branch: `main`.
- Require pull requests and the `CI / verify` check.
- Enable secret scanning and push protection.
- Enable private vulnerability reporting.
- Disable force pushes and branch deletion on `main`.
- Prefer squash merges and delete merged branches.
- Keep production `.env`, private keys, Ledger state, and generated OAuth users out of Git.

## Release artifacts

The downloadable release bundle contains:

```text
numtema-mcp-foundry-v1.3.0-sprint-1.3.zip
release/numtema-mcp-foundry-1.3.0.tgz
```

Verify hashes before installation using the values in the v1.3 verification report.
