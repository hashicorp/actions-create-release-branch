# Create Release Branch Action

Creates a new release branch based on the repo's ``version/VERSION`` file contents.

_This is intended for internal HashiCorp use only_

## Usage

- Make sure your repo's service account is configured to bypass branch protection rules on ``main``.

- Create a local workflow called ``create-release-branch.yml`` and include the following:

    ```
    name: Create a release branch
    on:
        - workflow_dispatch
    jobs:
    create-branch:
        runs-on: [linux, small]
        steps:
            - uses: actions/checkout@v3
            - uses: hashicorp/actions-create-release-branch@v1
                with:
                token: ${{ secrets.ELEVATED_GITHUB_TOKEN }}
    ```

- Run your workflow from the Github Actions UI.