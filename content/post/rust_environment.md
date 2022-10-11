---
title: "Rust Environment"
date: 2022-01-02T23:47:03-06:00
draft: false
category: Environments
tags:
- Development
- Rust
---

## Install Rust
{{< highlight bash >}}
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
{{< / highlight >}}

## Update Rust
{{< highlight bash >}}
rustup update
{{< / highlight >}}

## Cargo commands
{{< highlight bash >}}
cargo build  # build your project
cargo run  # run your project
cargo test  # test your project
cargo doc  # build documentation for your project
cargo publish  # publish a library to crates.io
{{< / highlight >}}

## Create new project
{{< highlight bash >}}
cargo new hello-rust  # Creates a new dir called hello-rust

hello-rust
|- Cargo.toml
|- src
  |- main.rs
{{< / highlight >}}

## CI Steps
{{< highlight bash >}}
cargo build
cargo test  # Run Tests
cargo tarpaulin --ignore-tests  # Code Coverage (install using 'cargo install cargo-tarpaulin')
cargo clippy -- -D warnings  # Linting (fail with warnings)
cargo fmt -- --check  # Format (fail with unformat)
cargo audit  # Security Audit
{{< / highlight >}}
