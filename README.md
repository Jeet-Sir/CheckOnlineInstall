# Setting Up Stellar Development Environment in GitHub Codespaces

This document outlines the steps taken to set up a Stellar smart contract development environment using GitHub Codespaces. It details the initial setup, the creation and deployment of a "Hello World" smart contract, and importantly, the issues encountered and their resolutions.

## Initial Setup

1.  **Opened a new GitHub Codespace:** We started by creating a new Codespace, which provides a pre-configured development environment in the cloud.

2.  **Installed Rust and the `wasm32-unknown-unknown` target:**
    ```bash
    curl --proto '=https' --tlsv1.2 -sSf [https://sh.rustup.rs](https://sh.rustup.rs) | sh
    rustup target add wasm32-unknown-unknown
    ```
    This ensured we had the necessary Rust toolchain and the target for compiling WebAssembly, which is required for Soroban smart contracts.

3.  **Installed the Stellar Command-Line Interface (CLI):**
    ```bash
    cargo install --locked stellar-cli@22.6.0 --features opt
    ```
    This command downloads and installs the `stellar-cli` tool, which is essential for interacting with the Stellar network and managing smart contracts.

## Encountered Errors and Resolutions

During the installation of `stellar-cli`, we faced the following errors:

### Error 1: Missing `libdbus-1` dependency

**Resolution:** This error indicated that the system library `libdbus-1` was missing in the Codespace environment. We resolved this by installing the necessary development packages using the following commands:

```bash
sudo apt update
sudo apt install -y libdbus-1-dev pkg-config
```
### Error 2: Missing libudev dependency
```bash
sudo apt update
sudo apt install -y libudev-dev
```
