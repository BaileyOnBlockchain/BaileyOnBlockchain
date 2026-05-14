# Don BaileyOnBlockchain
> Solo builder. Privacy maximalist. Encryption by default.  
> 5 years in. No team. No VC. No shortcuts.

---

<div align="center">

[![X](https://img.shields.io/badge/@blockchainbail-000000?style=flat&logo=x&logoColor=white)](https://x.com/blockchainbail)
[![X Project](https://img.shields.io/badge/@odennetworkXR-0052FF?style=flat&logo=x&logoColor=white)](https://x.com/odennetworkXR)
[![YouTube](https://img.shields.io/badge/@BailOnBlockchain-FF0000?style=flat&logo=youtube&logoColor=white)](https://www.youtube.com/@BailOnBlockchain)
[![Kick](https://img.shields.io/badge/blockchainbailey-53FC18?style=flat&logo=kick&logoColor=black)](https://kick.com/blockchainbailey)
[![Website](https://img.shields.io/badge/odennetworkxr.com-4C1D95?style=flat&logo=vercel&logoColor=white)](https://odennetworkxr.com)

</div>

---

## What I'm Building

### [Oden Network XR](https://odennetworkxr.com)
Privacy-first decentralised social dapp — built solo, end to end, on Base L2.

Not a wrapper. Not a template. Every system below was designed, coded, and shipped by one person.

**Encrypted Messaging** **(O-Chat)** & **(XRGroups)**
- End-to-end encrypted direct messaging via **XMTP V3** — multi-device session management, installation limit recovery, attachment support, real-time conversation streaming
- **Encrypted group chat** — Discord-style architecture with text channels, voice channels (Opus codec), role-based access, nuclear self-delete messages, and real-time group events

**Zero-Knowledge & Anonymous Posting** **(XRFeed)**
- **ZK anonymous posts** via **Semaphore + Groth16** — identity commitments, nullifier hashing, on-chain verification. Post without leaving a trace
- **Self-nuking posts** — auto-delete timestamps baked at the protocol level
- **AI content moderation** with proof generation

**On-Chain Systems (Base L2)**
- `XR_TOKEN` — ERC-20 with tipping, burning, permit
- `PRIVNET` — post management, earnings, tip routing
- `STAKING_VAULT` — lock periods, yield mechanics
- `SEMAPHORE` — ZK group proof verification
- `PROFILE_NFT` — on-chain profile verification
- `SCAM_REPORTS` — community scam registry
- **EIP-4337 Account Abstraction** — paymaster for gasless transactions

**Reputation & Trust**
- **Sovereignty Score (0–100)** — wallet age, transaction depth, protocol diversity, cross-chain activity, sybil flags. Not a vibe. Maths
- **Gitcoin Passport** integration, community scam reporting, multi-factor reputation

**Trading Intelligence**
- **AI-powered trading signals** — confidence scoring, entry/exit targets, risk/reward ratios
- **16+ technical indicators** — RSI, MACD, Bollinger Bands, EMA (20/50/200), Stochastic RSI, Williams %R, ROC, ADX, ATR, support/resistance, market regime detection
- **Multi-source price feeds** — Binance, CoinGecko, Jupiter with fallback routing

**Dead Man's Switch**
- On-chain cryptographic dead man's switch — encrypted last words, time-locked triggers, beneficiary configuration, multi-alert architecture

→ [Launch dApp](https://odennetworkxr.com) · [@odennetworkXR](https://x.com/odennetworkXR)

---

## Contract Work

### CTX Protocol — *Ongoing*
Active contract building on-chain intelligence and risk tooling for [CTX Protocol](https://ctx.xyz).

**Liquidation Cluster & Squeeze Risk Intelligence**  
Python-based system for analysing liquidation cluster formations, short squeeze probability, and real-time on-chain risk signals across DeFi markets. Built for protocol-level risk management — not the kind of thing you open-source.

**Token Launch Screener**  
MCP server that gives AI agents real-time token launch screening capabilities — new pair detection, liquidity analysis, risk flags, and launch signal scoring. Plugs directly into Claude and other MCP-compatible agents.

> CTX Protocol brought me in because the work is real. The systems above speak for themselves.

---

## Open Source

### [Wallet-Fingerprint-Detector](https://github.com/BaileyOnBlockchain/Wallet-Fingerprint-Detector)
CLI tool that classifies EVM wallets by on-chain behaviour — bots, whales, devs, rug pullers, and degens — across Ethereum and Base.

Built in TypeScript with ethers.js v6. Pulls transaction history, token transfers, internal txs, and RPC data, then runs five weighted classifiers to produce a probabilistic profile with a full terminal report.

**What it detects:**
- **BOT / SNIPER** — same-block txs, sub-3s burst windows, zero failure rate across large samples, algorithmic gas pricing, Flashbots relay interactions
- **WHALE** — balance >100 ETH, large single txs, institutional bridge usage (Across, Stargate, Hop), long-term token holds
- **DEV** — contract deployments, funded-then-deployed pattern, multisig factory interactions, team fund distribution, early token interactor
- **RUGGER** — Tornado Cash / mixer interactions, deploy→collect→dump→silence lifecycle, LP removal, serial deployer pattern
- **DEGEN** — DEX aggregator swaps, >50 unique tokens, high failed tx rate, launch sniping within 5 min, multi-chain activity

**Outputs:** Suspicion Index, Sophistication Index, weighted signal breakdown, JSON mode, file export, batch analysis, side-by-side wallet comparison.

---

### [Stealth-Address-Generator](https://github.com/BaileyOnBlockchain/Stealth-Address-Generator)
Complete TypeScript toolkit for **EIP-5564 stealth addresses** on Base L2 — the same privacy model as Monero, implemented natively on EVM.

Publish one meta-address. Anyone can derive a fresh one-time address only you can detect and spend from. Nothing on-chain links the payment back to you.

**What it does:**
- **Generate** — creates spending + viewing keypairs, derives a `st:base:0x…` meta-address, saves both private keys to an AES-256-GCM encrypted keystore (scrypt N=131072)
- **Send** — takes a recipient's meta-address, computes a one-time stealth address via secp256k1 ECDH, outputs the stealth address + EIP-5564 Announcer calldata
- **Scan** — fetches all `Announcement` events, pre-filters with view-tags (1/256 require full EC check) to find payments belonging to your viewing key
- **Spend** — derives the stealth private key from `(s + h) mod n`, verifies the address matches, and outputs the key for immediate sweeping
- **Registry** — register and resolve meta-addresses on-chain via the EIP-6538 Registry

Built on `@noble/curves` for raw secp256k1 ECDH — no wrappers, no shortcuts.

---

### [WalletConnectFixer](https://github.com/BaileyOnBlockchain/WalletConnectFixer)
Fixes for common WalletConnect + wagmi + Reown AppKit mobile connection failures.  
Documented and open-sourced after debugging actual root causes in production.

**Problems solved:**
- MetaMask silently auto-approving stale WC sessions without a signing prompt
- Opera GX / third-party `isMetaMask` injections hijacking the auth flow
- WC handshake dropping due to async IndexedDB race on session clear
- AppKit two-step flow interrupted by premature timeout logic
- Auto network-switch prompt on connect for chain-specific dapps

---

## Other Things I've Built

**AI & Agents**
- **Grok Cracked** — terminal-native agentic coding assistant. Full tool loop: file editing, bash, ripgrep, MCP server support, streaming Ink UI
- **Hansel** — multimodal AI bot. Multi-API routing, image analysis, voice recognition, Solana trading execution. Runs on a Pi
- **Private AI Node** — multi-model system running 24/7 on a private server. Always online. Not on GitHub. Not for sale
- **Telegram Bot Ecosystem** — multi-provider AI routing (Groq, Claude, OpenRouter), voice I/O, on-chain execution

**Quant & Trading**
- **Solana Scalping Bot** — live on mainnet. RSI/MACD/BB signals, dip-buying logic, autonomous risk management. Real money. Not a demo
- **AI Crypto Quant** — PyTorch price forecasting, backtester with equity curves + Sharpe ratio
- **Financial Tooling Suite** — portfolio tracking, P&L dashboards, quant signal engines, market data pipelines

**Security & Systems**
- **OSINT & Recon Frameworks** — data aggregation, footprint mapping. Built to understand exposure
- **Network Security Research** — packet analysis, vulnerability scanning, penetration testing tooling
- **Cryptographic Security Models** — encryption strength testing, key exchange protocols, attack resistance
- **ECU & Automotive Data** — T8Suite, binary map analysis, custom ignition timing workflows
- **Phone GPS Tracker** — real-time location tracking, live map rendering, mobile-first

**Tools**
- **RemindHUB** — local-first productivity dashboard. Task manager, quant signals, live news, canvas draw pad, Pomodoro. One Node.js server

---

## Stack

| Language | Frameworks | Web3 & Infra |
|---|---|---|
| ![TS](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white) | ![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat&logo=nextdotjs&logoColor=white) | ![Solidity](https://img.shields.io/badge/Solidity-363636?style=flat&logo=solidity&logoColor=white) |
| ![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white) | ![React](https://img.shields.io/badge/React-20232A?style=flat&logo=react&logoColor=61DAFB) | ![Base](https://img.shields.io/badge/Base_L2-0052FF?style=flat&logo=coinbase&logoColor=white) |
| ![JS](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black) | ![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat&logo=nodedotjs&logoColor=white) | ![XMTP](https://img.shields.io/badge/XMTP-000000?style=flat&logo=ethereum&logoColor=white) |
| ![Rust](https://img.shields.io/badge/Rust-000000?style=flat&logo=rust&logoColor=white) | ![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white) | ![wagmi](https://img.shields.io/badge/wagmi-1C1C1C?style=flat&logo=ethereum&logoColor=white) |
| ![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat&logo=gnubash&logoColor=white) | ![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white) | ![Solana](https://img.shields.io/badge/Solana-9945FF?style=flat&logo=solana&logoColor=white) |
| ![Binary](https://img.shields.io/badge/Binary_Analysis-555555?style=flat&logo=buffer&logoColor=white) | ![Prisma](https://img.shields.io/badge/Prisma-2D3748?style=flat&logo=prisma&logoColor=white) | ![Semaphore](https://img.shields.io/badge/Semaphore_ZK-4C1D95?style=flat&logo=ethereum&logoColor=white) |
| | ![Raspberry Pi](https://img.shields.io/badge/Raspberry_Pi-A22846?style=flat&logo=raspberrypi&logoColor=white) | ![EIP4337](https://img.shields.io/badge/EIP--4337_AA-363636?style=flat&logo=ethereum&logoColor=white) |

---

## The Ethos

- **Privacy is a right** — not a feature, not a setting, not optional
- **Ownership belongs to users** — not platforms, not VCs, not algorithms
- **Decentralisation is the only honest answer**
- **Zero-knowledge is the future** — prove anything, reveal nothing

---

*No degree. No team. Just shipping.*
