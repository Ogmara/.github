# Ogmara

Decentralized chat and news platform built on the [Klever](https://klever.org) blockchain. [ogmara.org](https://ogmara.org)

**No central servers. No gatekeepers. You own your identity and your data.**

## What is Ogmara?

Ogmara is a three-layer communication platform:

- **Klever Mainnet** — Your identity is a blockchain address. You sign messages with your own keys.
- **L2 Node Network** — A distributed network of nodes that store and relay chat messages and news content. Anyone can run a node.
- **IPFS** — Media (images, videos, files) is stored on the decentralized IPFS network.

## Run a Node

The easiest way to join the Ogmara network. Requires [Docker](https://docs.docker.com/engine/install/).

```bash
docker pull ogmara/ogmara:l2-node-latest

mkdir -p ~/ogmara-node
curl -sO https://raw.githubusercontent.com/Ogmara/l2-node/main/ogmara.example.toml
mv ogmara.example.toml ~/ogmara-node/ogmara.toml

docker run -d --name ogmara-node --restart unless-stopped \
  -v ~/ogmara-node/ogmara.toml:/etc/ogmara/ogmara.toml:ro \
  -v ogmara-data:/data \
  -p 41720:41720/udp -p 41720:41720/tcp -p 41721:41721 \
  ogmara/ogmara:l2-node-latest

# Verify
curl -s http://localhost:41721/api/v1/health
```

Testnet defaults are pre-filled — the node connects to the network immediately.

For media support, also run an [IPFS node](https://docs.ipfs.tech/install/) or use the [docker-compose.yml](https://github.com/Ogmara/l2-node/blob/main/docker-compose.yml) that includes both.

See the [Node Operator Guide](https://github.com/Ogmara/ogmara/blob/main/docs/guides/node-operator-guide.md) for full details.

## Repositories

| | Repo | Description |
|---|------|-------------|
| 🔧 | [l2-node](https://github.com/Ogmara/l2-node) | L2 network node (Rust) — **run your own node** |
| 📜 | [smart-contract](https://github.com/Ogmara/smart-contract) | Klever KApp smart contract |
| 🦀 | [sdk-rust](https://github.com/Ogmara/sdk-rust) | Rust client SDK |
| 📦 | [sdk-js](https://github.com/Ogmara/sdk-js) | JavaScript/TypeScript client SDK |
| 🌐 | [web](https://github.com/Ogmara/web) | Web frontend (PWA) |
| 🖥️ | [desktop](https://github.com/Ogmara/desktop) | Desktop app (Tauri) |
| 📱 | [mobile](https://github.com/Ogmara/mobile) | Mobile app (React Native) |
| 🔔 | [push-gateway](https://github.com/Ogmara/push-gateway) | Push notification service |
| 🌍 | [website](https://github.com/Ogmara/website) | ogmara.org — landing page + network dashboard |
| 📋 | [ogmara](https://github.com/Ogmara/ogmara) | Specifications and architecture docs |

## Get Involved

- **Run a node** — `docker pull ogmara/ogmara:l2-node-latest` and [join the network](https://github.com/Ogmara/l2-node)
- **Use the app** — [ogmara.org/app](https://ogmara.org/app/)
- **Build on Ogmara** — [sdk-js](https://github.com/Ogmara/sdk-js) or [sdk-rust](https://github.com/Ogmara/sdk-rust)
- **Read the specs** — [Protocol](https://github.com/Ogmara/ogmara/blob/main/docs/specs/01-protocol.md), [L2 Node](https://github.com/Ogmara/ogmara/blob/main/docs/specs/03-l2-node.md), [On-Chain](https://github.com/Ogmara/ogmara/blob/main/docs/specs/02-onchain.md)

## License

MIT
