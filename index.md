---
fonts: Literata
css: |
  h3, h4 { font-family: Literata; font-weight: 400 }
  a { color: #ffd5aa }
---

Hi, I'm Raymond!

I'm working on multi-user AI interfaces, interoperability, and new agent platforms.

Previously I was a cofounder at Commonwealth, an early DAO/governance tool, which raised $20m+ and was used by hundreds of protocols. I designed and built the product.

Before that, I was at AngelList, Facebook, Medium, and founding engineer at a company building predictive analytics for political intelligence.

### Projects

#### HCI/AI Projects (2026)

Human-computer interface experiments using modern language models.

- A Quora-like knowledge graph and social network for people to help each other answer questions with AI.
- A recursive summarization system that created concise bullet-point outlines, to distill books of up to hundreds of pages. Collaborated with [avichalp](https://avichalp.me/).
- An Obsidian-like document editor with AI, that uses Git repos for data portability. You can read about this in [[Backendless Software]]. Input is [open source](https://github.com/inputmd/input).

#### [TEEKit](https://teekit.org) (2025)

A JS runtime using Trusted Execution Environments, a class of technologies that allows users to "verify" that server CPUs are running particular code.

This project involved several components:

- An encrypted WebSocket tunnel that embeds inside browser applications, to create verifiable connections to TEEs using DH key exchange and stream encryption.
- A workerd/V8-based JS runtime, deployed inside the TEE, that hosts Hono web applications and provides core services like a database and networking.
- A reproducible Debian image, that launches workerd, acquires SSH certificates, and attests to the specific JS code running inside. We extended a well-known mkosi implementation by [Flashbots](https://github.com/flashbots/flashbots-images).

All together, these components can be used as a serverless smart contract environment, where anyone can deploy JS code, users can privately store their data, and no crypto is required.

We found a number of prospective users, including a few that built demos using our library, but put the project on hold because of the collapse of crypto communities and accelerating progress in AI.

In early 2026, Moxie Marlinspike created a similar system to our tunnel using [Noise](https://en.wikipedia.org/wiki/Noise_Protocol_Framework) for Confer, his TEE/AI platform. There still isn't a widely available TEE host that allows arbitrary applications to be deployed, and allows users to verify that they're interacting with them (maybe there will be soon!).

#### [Canvas](https://github.com/canvasxyz/canvas) (2022-2025)

Canvas was a programmable peer-to-peer database, created as a spinout from my previous startup, which was hosting governance forums for hundreds of Ethereum and Cosmos projects at the time. We wanted to decentralize the backend so projects could build their own frontends and custom software to engage their communities.

To do this, we created a syntax for JS "smart contracts", essentially stored procedures written as JS functions, on top of a simple key-value database. By doing some clever bookkeeping, we built a causal graph of events that happened on different nodes simultaneously, which allowed us to specify deterministic logic for merging (or dropping) concurrent events.

This worked well enough that we ported a fairly complex [real-time game](https://www.pogiciv.com/) to our system. We also published a few research blog posts, including ones on [reliable broadcast for libp2p](https://joelgustafson.com/posts/2024-09-30/gossiplog-reliable-causal-broadcast-for-libp2p/) and [serializable transactions for peer-to-peer databases](https://joelgustafson.com/posts/2025-07-21/serializable-transactions-for-peer-to-peer-databases/).

#### Earlier Projects

- [Group Signatures with zkSNARKs](https://0xparc.org/blog/zk-group-sigs) (2021, 0xPARC Hack Week)
- [Declaration of Interdependence](https://verses.xyz/) (2021, with Verses)
- [Commonwealth] - Built the initial product and engineering team. Company later raised a seed round from [Dragonfly](https://www.coindesk.com/business/2021/05/18/common-protocol-raises-32m-to-streamline-defi-governance), and Series A from [Spark Capital](https://decrypt.co/100437/common-raises-20m-to-build-dao-management-platform-launch-token).
- [Princeton] - Undergraduae degree in computer science, research at the Center for Information Technology Policy.

#### Blogroll

[Jasmine Wang](https://substack.com/@jasminewang)
[Saffron Huang](https://saffronhuang.com/)
[Divya Siddarth](https://divyasiddarth.com/)
[Graham Johnson](https://suspendedreason.github.io/)
[Ivan Vendrov](https://www.vendrov.ai/)
[Snav](https://snavsoft.com/)
