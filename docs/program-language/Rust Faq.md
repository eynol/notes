---
layout: default
title: Rust FAQ
parent: Program Language
nav_order: 2
---

# Rust FAQ




## install inside


config upstream mirror in ~/.zshrc or ~/.bashrc

```bash
export RUSTUP_DIST_SERVER="https://rsproxy.cn"
export RUSTUP_UPDATE_ROOT="https://rsproxy.cn/rustup"
```

and then run command

```bash
curl --proto '=https' --tlsv1.2 -sSf https://rsproxy.cn/rustup-init.sh | sh

# official cmd
# curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```




config file `~/.cargo/config`
```bash
[source.crates-io]
replace-with = 'rsproxy-sparse'
[source.rsproxy]
registry = "https://rsproxy.cn/crates.io-index"
[source.rsproxy-sparse]
registry = "sparse+https://rsproxy.cn/index/"
[registries.rsproxy]
index = "https://rsproxy.cn/crates.io-index"
[net]
git-fetch-with-cli = true
```
