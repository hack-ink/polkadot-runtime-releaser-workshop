## Polkadot Runtime Releaser Workshop
This repository contains a production-ready polkadot-sdk-based runtime release setup.

### Override
> Why do we need to override the runtime?
>
> Always keep the on-chain runtime as minimal as possible which can help reduce the runtime size and improve the performance.
> Override with the `force-debug` runtime, you can get more debug information in the runtime log.
> Override with the `evm-tracing` runtime, you can enable the EVM tracing feature in the runtime.

1. Create a runtime-overrides repository for your runtime.
2. Copy and configure the [overrides](.github/workflows/override.yml) action to your runtime-overrides repository. With this action, you can maintain the runtime overrides in the runtime-overrides repository automatically and easily without need to build it every time when you need it and can provide this repository for other developers/users.
3. The action file has pretty detailed comments, you can follow the comments to configure the action. Please feel free to open an issue in this repository if you find any issues or have any questions.
4. Create the runtime branches in the runtime-overrides repository, otherwise the action will fail since it can not push the commit to the corresponding branch. The name should be the same as runtime crate time, for example, [`polkadot-runtime`](https://github.com/polkadot-fellows/runtimes/blob/2e73a6c90159b723c741b1a5b5898ba002c5e87d/relay/polkadot/Cargo.toml#L2), [`staging-kusama-runtime`](https://github.com/polkadot-fellows/runtimes/blob/2e73a6c90159b723c741b1a5b5898ba002c5e87d/relay/kusama/Cargo.toml#L7).

#### Workshop Example
- [Polkadot Runtime](https://github.com/hack-ink/polkadot-runtime-releaser-workshop/tree/polkadot-runtime)
- [Staging Kusama Runtime](https://github.com/hack-ink/polkadot-runtime-releaser-workshop/tree/staging-kusama-runtime)

### Try Runtime
1. Copy and configure the [try-runtime](.github/workflows/try-runtime.yml) action to your runtime repository.
2. The action file has pretty detailed comments, you can follow the comments to configure the action. Please feel free to open an issue in this repository if you find any issues or have any questions.
3. Open a PR to the runtime repository.
4. Comment `/bot try-runtime` in the PR, the action will run and comment the result in the PR.

#### Workshop Example
- [Try-Runtime](https://github.com/hack-ink/polkadot-runtime-releaser-workshop/pull/3)

### Release
1. Copy and configure the [release](.github/workflows/release.yml) action to your runtime repository.
2. The action file has pretty detailed comments, you can follow the comments to configure the action. Please feel free to open an issue in this repository if you find any issues or have any questions.
3. Add and push a tag to the runtime repository, the action will run and release the runtime in runtime repository and trigger the override for runtime-overrides repository.

#### Workshop Example
- [Release `v0.0.1`](https://github.com/hack-ink/polkadot-runtime-releaser-workshop/releases/tag/v0.0.1)
