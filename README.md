Penulis: [Naufal](https://x.com/0xfal)

> [!NOTE]
> **WHAT IS Miden?**\
> TBD.

# Tutorial Miden Node

## 1. Prerequisites

- [Cara terhubung ke VPS](https://github.com/ZuperHunt/Connect-to-VPS)

## 2. Requirements

### Hardware

| Part | Minimum | Recommended |
| ------------- | ------------- | ------------- |
| CPU | - | 2 cores |
| RAM | - | 4 GB |
| SSD | - | 50 GB |

### Software

| ✅ Linux | ✅ macOS | ✅ Windows (WSL) |
| ------------- | ------------- | ------------- |

> [!NOTE]
> Tutorial ini dibuat menggunakan Linux (Ubuntu), untuk sistem operasi lainnya mungkin akan sedikit berbeda!

## 3. Dependencies

### 3.1 System Packages

```
sudo apt update && sudo apt upgrade -y
```

### 3.2 Install Rust

Copy-paste, trus tinggal tekan enter aja.

```
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
. "$HOME/.cargo/env"
```

### 3.3 Install Other Essential Packages

```
sudo apt install build-essential libsqlite3-dev clang pkg-config libssl-dev git-all
```

## 4. Execution

### 4.1 Create a Session

Ubah `<SESSION_NAME>` menjadi terserahmu.

```
tmux new -s <SESSION_NAME>
```

### 4.2 Install the Node

```
cargo install miden-node --locked
```

### 4.3 Initializing the Node

```
miden-node store dump-genesis > genesis.toml
mkdir -p data accounts
miden-node bundled bootstrap \
  --data-directory data \
  --accounts-directory accounts \
  --config genesis.toml
```

### 4.4 Starting the Node

```
miden-node bundled start \
  --data-directory data \
  --rpc.url http://0.0.0.0:57123
```

---

Reach us if you have any question:\
ZuperCollective's [Discord server](https://discord.gg/ZuperCollective) | [X(Twitter)](https://twitter.com/ZuperCollective)

# Acknowledgements

* [Miden Docs](https://github.com/0xMiden/miden-tutorials/tree/main/node)
