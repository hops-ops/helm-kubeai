### What's changed in v0.1.0

* feat: helm chart xrd (by @patrickleet)

* fix: add model symlinks and RBAC for e2e tests (by @patrickleet)

  - Add model symlinks to tests/test-render and tests/e2etest-kubeai
  - Add ClusterRoleBinding for Helm provider permissions in e2e test
  - Add timeout settings matching other helm XRD e2e tests
  - Use Rapid channel for Crossplane upgrades

  Co-Authored-By: Claude Opus 4.5 <noreply@anthropic.com>


