# GitHub Actions runners

Linux jobs use repository variables; empty variables preserve the existing Blacksmith
runners. macOS and Windows jobs keep their existing labels.

After connecting Ubicloud Managed Runners to this repository, set:

| Repository variable        | Ubicloud label                         | Architecture |
| -------------------------- | -------------------------------------- | ------------ |
| `UBICLOUD_RUNNER_X64_16`   | `ubicloud-standard-16-ubuntu-2404`     | x64          |
| `UBICLOUD_RUNNER_ARM64_16` | `ubicloud-standard-16-arm-ubuntu-2404` | arm64        |

Both labels preserve the existing 16-vCPU size and Ubuntu 24.04. Premium routing
is enabled by default; check GitHub Runners → Settings and the applicable rate
before activating. Use repository-level variables, not environment-level variables.

Confirm actual runner names and labels in GitHub Actions and matching Ubicloud
jobs. Verify x64 checks and ARM Docker builds separately. To roll back, remove
the variables and cancel/rerun affected jobs. Already queued/running jobs do not
move automatically. Empty-variable fallback does not detect runner outages.

Workflow triggers, job steps, secrets, deployment/release rules, and Windows/macOS
runners retain their current configuration.

References: [setup](https://www.ubicloud.com/docs/github-actions-integration/quickstart),
[labels](https://www.ubicloud.com/docs/github-actions-integration/runner-types),
[pricing](https://www.ubicloud.com/docs/about/pricing).
