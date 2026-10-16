# Public GitHub metrics

This profile uses [lowlighter/metrics](https://github.com/lowlighter/metrics), pinned to release v3.34. Its workflow renders a single SVG once a week and on manual request. No GitHub Marketplace app or paid service is required.

## One-time token setup

The upstream Metrics action needs a token that can query a user profile. The repository-scoped automatic `GITHUB_TOKEN` cannot retrieve all those public profile statistics.

1. From the **brierfieldlabs** GitHub account, create a **personal access token (classic) with *no scopes selected***. Do **not** give it `repo`, `read:org`, `read:user` or other additional permissions. Give it a descriptive name and an expiry date. Never put it into Git or a README.
2. Open this profile repository's **Settings → Secrets and variables → Actions → New repository secret**.
3. Name the secret `METRICS_TOKEN` and enter the new no-scope token.
4. After the pull request is merged, choose **Actions → Public GitHub metrics → Run workflow** to create `github-metrics.svg`.
5. Check that the resulting image shows only information you want publicly displayed. Renew the token when it expires.

The job skips rendering without `METRICS_TOKEN` and explains this in the workflow summary. It never reads organisation or private-repository data using special scopes. We deliberately omit the contribution calendar, which can aggregate private contribution counts depending on GitHub profile preferences.

The workflow uses the repository's automatic `GITHUB_TOKEN` only for committing its generated `github-metrics.svg` into this public profile repository. The token's write permission applies to this repository, not other projects.

## Maintenance

- Schedule: Monday 08:17 UTC (09:17 BST in summer); manual runs are also available.
- Generated file: `github-metrics.svg`, linked from the root README.
- Action version: `lowlighter/metrics` v3.34 pinned to its full commit SHA. Update it deliberately after reviewing a newer release.
- No third-party secrets, private repository names, private metrics or personal account credentials belong in this public repository.
