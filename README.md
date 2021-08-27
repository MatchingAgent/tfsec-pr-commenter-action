# tfsec-pr-commenter-action
Add comments to pull requests where tfsec checks have failed

To add the action, add `tfsec_pr_commenter.yml` into the `.github/workflows` directory in the root of your Github project.

The contents of `tfsec_pr_commenter.yml` should be;

```yaml
name: tfsec-pr-commenter
on:
  pull_request:
jobs:
  tfsec:
    name: tfsec PR commenter
    runs-on: ubuntu-latest

    steps:
      - name: Clone repo
        uses: actions/checkout@master

      - name: tfsec
        uses: aquasecurity/tfsec-pr-commenter-action@main
        with:
          github_token: ${{ github.token }}
```

On each pull request and subsequent commit, tfsec will run and add comments to the PR where tfsec has failed. 

The comment will only be added once per transgression.

## Example PR Comment

The screenshot below demonstrates the comments that can be expected when using the action
<img src="https://user-images.githubusercontent.com/62197019/131106406-6380b66a-672d-44d7-bdb1-2e2da4e5db10.png" height="400px">
