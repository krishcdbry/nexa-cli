# Nexa CLI

**Interactive command-line interface for NexaDB**

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Rust](https://img.shields.io/badge/rust-1.70+-orange.svg)](https://www.rust-lang.org/)

Nexa is a fast, zero-dependency CLI tool for NexaDB written in Rust. Think `mysql` for MySQL, but `nexa` for NexaDB.

## ✨ Features

- ✅ **Zero dependencies** - Single standalone binary
- ✅ **Blazing fast** - Written in Rust, uses MessagePack binary protocol
- ✅ **Cross-platform** - Works on Linux, macOS, Windows
- ✅ **Full-featured** - All CRUD operations, vector search, aggregation
- ✅ **Interactive** - REPL with readline support and command history
- ✅ **Secure** - Password-based authentication

## 🚀 Installation

### Linux

```bash
# x86_64 (Intel/AMD)
curl -fsSL https://github.com/krishcdbry/nexa-cli/releases/latest/download/nexa-x86_64-unknown-linux-gnu -o nexa
chmod +x nexa
sudo mv nexa /usr/local/bin/

# aarch64 (ARM64 - Raspberry Pi, AWS Graviton)
curl -fsSL https://github.com/krishcdbry/nexa-cli/releases/latest/download/nexa-aarch64-unknown-linux-gnu -o nexa
chmod +x nexa
sudo mv nexa /usr/local/bin/
```

### macOS

```bash
# Apple Silicon (M1/M2/M3)
curl -fsSL https://github.com/krishcdbry/nexa-cli/releases/latest/download/nexa-aarch64-apple-darwin -o nexa
chmod +x nexa
sudo mv nexa /usr/local/bin/

# Intel Macs
curl -fsSL https://github.com/krishcdbry/nexa-cli/releases/latest/download/nexa-x86_64-apple-darwin -o nexa
chmod +x nexa
sudo mv nexa /usr/local/bin/
```

### Or install NexaDB with nexa included

```bash
# Homebrew (macOS)
brew install nexadb

# Linux installer (includes nexa)
curl -fsSL https://github.com/krishcdbry/nexadb/releases/latest/download/install.sh | bash
```

## 📖 Usage

```bash
# Start interactive session
nexa -u root -p
Password: ********

# Or specify password directly (for scripts)
nexa -u root -p nexadb123

# Custom host/port
nexa -h 192.168.1.100 -P 6970 -u root -p
```

### Commands

```
nexa> help
Available commands:
  collections          - List all collections
  use <name>          - Switch to collection
  insert <json>       - Insert document
  read <id>           - Read document by ID
  query <json>        - Query documents
  update <id> <json>  - Update document
  delete <id>         - Delete document
  count               - Count documents in current collection
  vector_search <vec> <limit> <dims> - Vector similarity search
  exit                - Exit nexa
```

### Examples

```bash
nexa> collections
✓ Found 2 collection(s):
  [1] movies
  [2] users

nexa> use movies
✓ Switched to collection 'movies'

nexa(movies)> insert {"title": "The Matrix", "year": 1999}
✓ Document created: doc_abc123

nexa(movies)> query {"year": {"$gte": 2000}}
✓ Found 5 document(s)

nexa(movies)> count
✓ Document count: 127

nexa(movies)> exit
Goodbye! 👋
```

## 🛠️ Building from Source

```bash
# Clone the repository
git clone https://github.com/krishcdbry/nexa-cli.git
cd nexa-cli

# Build release binary
cargo build --release

# Binary will be in target/release/nexa
./target/release/nexa --version
```

### Cross-compilation

```bash
# Install cross-compilation toolchains
rustup target add x86_64-unknown-linux-gnu
rustup target add aarch64-unknown-linux-gnu
rustup target add x86_64-apple-darwin
rustup target add aarch64-apple-darwin

# Build for target
cargo build --release --target x86_64-unknown-linux-gnu

# Or use the build script
./build.sh
```

## 📝 License

MIT License - See [LICENSE](LICENSE) file

## 🔗 Links

- **NexaDB**: https://github.com/krishcdbry/nexadb
- **Documentation**: https://nexadb.io/docs
- **Website**: https://nexadb.io

---

<div align="center">

**Built with ❤️ by the NexaDB Team**

[⭐ Star on GitHub](https://github.com/krishcdbry/nexa-cli) • [📖 NexaDB Docs](https://nexadb.io/docs)

</div>
