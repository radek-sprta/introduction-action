<!-- BEGIN_GITHUB_DOCS_BLOCK -->
# Introduction Profile README

**Type**: composite

**Description**: Compose a profile README with the [introduction](https://crates.io/crates/introduction) crate and push it to a repository.

## Inputs

| Name | Description | Default | Required | Deprecation Message |
|------|-------------|---------|----------|---------------------|
| target-repository | Repository to update, in owner/name form. | ${{ github.repository }} | false | N/A |
| github-token | GitHub token used to clone and push. Pushing to another repository requires a PAT. | ${{ github.token }} | false | N/A |
| gitlab-token | GitLab token used to fetch GitLab contributions. |  | false | N/A |
| template-file | Path to the README template. | template.md | false | N/A |
| config-file | Path to the introduction config file. | .introduction.toml | false | N/A |
| version | Version of the introduction crate to install. | 0.2.0 | false | N/A |


<!-- END_GITHUB_DOCS_BLOCK -->

## Usage

```yaml
on:
  schedule:
    - cron: "28 9 * * 1"
  workflow_dispatch:

jobs:
  update-readme:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v6
      - uses: radek-sprta/introduction-action@main
        with:
          target-repository: owner/owner
          github-token: ${{ secrets.TARGET_REPO_TOKEN }}
          gitlab-token: ${{ secrets.GITLAB_TOKEN }}
```

The checked-out repository must contain the template and config files.

For more information about the template and config files, see the [introduction crate documentation](https://crates.io/crates/introduction).