# Mathew Stevens

Full-stack software engineer building live products across web, mobile, backend systems, real-time infrastructure, SDKs, developer tools, AI-agent workflows, and AI evaluation systems.

I solo-built and launched Agentic and SolPulse: two production products with 1,750+ combined users, 60+ reviews, 4.2★–4.3★ ratings, app store releases, and real production usage.

## Shipped Products

### [Agentic](https://agentic-signer.com) - Multi-Wallet AI Agent Signer

 AI-agent wallet application where agents prepare wallet actions and external payment requests while users approve through their own wallets. Live across web, iOS, Android, desktop, CLI, MCP tools, and SDK surfaces.

- **Traction** — 1,000+ users in 2 months, 4.2★ rating, 36 reviews.
- **Non-custodial approval model** — Agents propose actions; users approve with their own wallets; private keys never leave the device.
- **Agent workflows** — Research tokens/wallets, check market conditions, set constraints, and prepare sends, swaps, limit orders, DCA schedules, lending/borrowing moves, and message/transaction signing.
- **Shared agent/payment architecture** — One WalletBackend powers browser app, mobile paths, desktop shell, CLI, MCP tools, Vercel AI tools, Solana Agent Kit adapter, A2A AgentCard metadata, and AP2/ACP/MPP payment- adapter flows.
- **Production signing UX** — Approval polling, transaction simulation, sign-and-send flows, Wallet Standard support, and live wallet review cards inside chat.

### [SolPulse](https://solpulse.trade) - Real-Time Trading Platform

Solo-built production trading platform across web, iOS, and Android with 800+ users, 26 reviews, and a 4.3★ rating.

- **Execution engine** — DCA, limit orders, smart TP/SL exits, routing, priority-fee controls, execution logs, and 1,200 concurrent transaction monitors at 10ms intervals.
- **35 intelligence signals** — Token risk, liquidity, smart-money activity, dev identity, rug/fraud detection, whale activity, and real-time filters.
- **Risk controls** — Max daily loss limits, per-trade risk caps, portfolio buckets, and regime-aware controls exposed through a consumer UI.
- **Full stack** — React/Vite, Node/Express, PostgreSQL/Prisma, Redis, WebSockets, SSE, backend APIs, database design, frontend UX, mobile releases, and production support.
- **Non-custodial signing** — Wallet approval flows where private keys remain inside user wallets/devices.


## AI Systems and Evaluation

### [Klavis Terminal-Bench 3 Durable Outbox Benchmark](https://github.com/mstevens843/terminal-bench-durable-outbox)

**6/6 frontier agents failed with clean reward-0 results.** Original Terminal-Bench 3 task modeling a durable approval outbox: turning an approved AI action into an executed external action exactly once while workers crash mid-call, deliveries duplicate, approvals are revoked, and the external tool returns `UNKNOWN` before an authoritative receipt arrives.

- **6/6 clean reward-0 trials** — 3 Claude Opus runs and 3 OpenAI Codex runs failed without timeouts, API errors, or orphaned runs; the reference implementation passes 267/267 checks.
- **Real false-positive failures** — Agents produced locally plausible implementations that still mishandled `UNKNOWN` outcomes, receipt reconciliation, revocation, exactly-once execution, progress, or audit-state legality. 
- **Adversarial verifier hardening** — Built isolated tool-ledger collection, process separation, root-only controls, unprivileged execution, cheat oracles, and deterministic reward checks to prevent reward-hacking paths.

### [ConfigPilot](https://github.com/mstevens843/ConfigPilot) - AI Fund / Andrew Ng OEM Decision Engine

Built for an AI Fund / Andrew Ng team challenge around applying AI to B2B OEM decision-making.

ConfigPilot is an AI-assisted OEM configuration engine where an LLM proposes commercial recommendations, then deterministic guardrails verify whether those recommendations are safe against margin, inventory, lead-time, policy, and audit constraints before approval.

- **AI + deterministic controls** — LLM proposes OEM recommendations; business rules verify margin, inventory, lead-time, policy, and audit constraints before approval.
- **Full-stack decision workflow** — Built the working demo across frontend, backend, validation logic, recommendation review, and approval flow.
- **Business-facing AI system** — Focused on practical AI adoption for B2B commercial decision-making, not open-ended chat.


## Open-Source Infrastructure

### [iOS Native Wallet Adapter](https://github.com/mstevens843/ios-solana-wallet-adapter)

Swift Package for iOS-native wallet deeplink signing across Phantom, Solflare, and Backpack.

- **Encrypted transport** — X25519 ephemeral keys, NaCl box encryption, Base58 encoding, callback decoding, nonce/session handling, and wallet error mapping.
- **iOS lifecycle support** — SwiftUI/UIKit URL routing, pending request cancellation, Keychain-backed state, and deterministic smoke-test logging.
- **Wallet picker UX** — Phantom, Solflare, Backpack, and Jupiter Mobile support with remembered wallet preference.
- **MWA-style app semantics** — `authorize`, `deauthorize`, `signMessages`, `signTransactions`, `signAndSendTransactions`, `getCapabilities`, and SIWS-style flows over iOS deeplink transport.

### [TxShield](https://github.com/mstevens843/solana-tx-guard) - Transaction Safety Layer

Open, embeddable pre-sign transaction safety system for wallets, dApps, trading UIs, mobile apps, and agent signing flows.

- **Static analyzer** — Decodes raw transactions locally and flags risky patterns before signature.
- **Drain detection rules** — Durable nonce abuse, authority changes, token approvals, system assigns, suspicious writable accounts, and wallet-drainer primitives.
- **Simulation and diff layer** — Optional RPC enrichment for inner-CPI walking, balance/owner/delegate diffs, and divergence checks.
- **Embeddable packages** — TypeScript core, rules, registry, simulation, React hooks/components, and CLI scanner for browser apps, Node, React Native, Capacitor, and CI gates.

## SDKs and Engine Integrations

### [Cocos Creator Mobile Wallet Adapter SDK](https://github.com/mstevens843/Cocos-Solana-MWA-SDK)

First Mobile Wallet Adapter SDK for Cocos Creator, built from scratch.

- TypeScript API, native Android bridge, ECDH/AES-GCM wallet association, SIWS, message signing, transaction signing, sign-and-send flows, auth caching, and multi-wallet support.
- Hardware-verified with Phantom, Solflare, Backpack, Jupiter, and Seed Vault on Seeker.
- Includes Token Duel demo game proving real on-chain gameplay flows.

### [Unreal Engine 5 Mobile Wallet Adapter SDK](https://github.com/mstevens843/unreal-solana-mwa)

First production-ready Mobile Wallet Adapter plugin for Unreal Engine 5.

- Kotlin clientlib, C++ JNI bridge, Blueprint UFUNCTION surface, auth caching, SIWS, signing, sign-and-send, capabilities, and multi-wallet support.
- Exposes native MWA, sign-then-broadcast fallback, and auto routing for wallet compatibility.
- Hardware-verified with Phantom, Solflare, Backpack, Jupiter, and Seed Vault on Seeker.

### [Capacitor Mobile Wallet Adapter](https://github.com/mstevens843/capacitor-solana-mobile-wallet-adapter)

Capacitor plugin for native Android Mobile Wallet Adapter support from hybrid mobile apps.

### [Godot Mobile Wallet Adapter Example](https://github.com/mstevens843/godot-solana-mwa-example)

Multi-wallet Godot example app and SDK integration work.

- Seeker hardware verification across Seed Vault, Phantom, Solflare, Backpack, and Jupiter.
- Merged upstream PRs for reconnect/full state reset, getCapabilities, sign-and-send bridge support, SIWS wallet-proof APIs, and auth-token caching.

### [Unity Mobile Wallet Adapter Example](https://github.com/mstevens843/unity-solana-mwa-example)

Unity wallet adapter example app and SDK integration work.

- Found 11 integration bugs during hardware testing.
- Built auth-token caching, reconnect flows, deterministic logging, and MWA 2.0 API coverage.
- Merged upstream WebGL wallet auto-select UX fix.

## What I Work With

TypeScript, JavaScript, React, Vite, Node.js, Express, PostgreSQL, Prisma, Redis, WebSockets, SSE, REST APIs, Swift, SwiftUI, Kotlin, Java, C#, C++, GDScript, Capacitor, Unity, Unreal
Engine, Godot, Cocos Creator, SDK engineering, CLI tools, MCP, Vercel AI SDK, wallet integrations, non-custodial signing flows, and production support.

## Links

- [Portfolio](https://mathewstevens.dev/portfolio/)
- [LinkedIn](https://www.linkedin.com/in/mathewbradleystevens)
- [Twitter / X](https://twitter.com/mattinfra)
