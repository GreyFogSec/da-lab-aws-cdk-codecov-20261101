# AWS CDK Codecov artifact-boundary lab

This public lab mirrors the relevant `aws/aws-cdk` workflow shape:

- a read-only `pull_request` producer uploads `coverage-artifacts`;
- a trusted `workflow_run` consumer has `contents: write`, `id-token: write`, and `actions: read`;
- trusted default-branch code is checked out before `actions/download-artifact@v8` writes into the repository tree;
- a harmless release containing only hashes proves the effective privileged operation.

The committed `packages/aws-cdk-lib/core/coverage` symlink is an **artificial positive-control prerequisite**. It is absent from the real AWS CDK repository. A successful run demonstrates the Action-level pre-existing-symlink primitive, not a vulnerability in AWS CDK.

No production credentials or resources are used.
