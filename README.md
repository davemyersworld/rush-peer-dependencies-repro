# Repro steps

This repository demonstrates the bug in @microsoft/rush in which RushInstallManager incorrectly installs peerDependencies, even when pnpm's `auto-install-peers=false` (also when `pnpmOptions.autoInstallPeers: false`).

1. Run `rush update`
2. Run `ls -la apps/package-with-peer-dep/node_modules`

Expected: One dependency: `react`
Actual: Two dependencies (`react` and `react-router`).


Note: With `useWorkspaces:true`, we see the correct behavior, `react-router` is not installed. 