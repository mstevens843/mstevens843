  # Mathew Stevens                                                                                                                                                                                                                                                            
                                                                                                                                                                                                                                                                              
   Full-stack Solana developer. I build production trading infrastructure, automated execution systems, and cross-platform mobile wallet integrations.                                                                                                                       
                                                                                                                                                                                                                                                                              
   ## Projects                                                                                                                                                                                                                                                               

   ### [SolPulse](https://solpulse.trade) - Solana Trading Platform                                                                                                                                                                                                          
   Automated trading platform with a multi-pillar intelligence engine, real-time execution, and institutional-grade risk management — built solo. Web, iOS, Android. Listed on the Solana dApp Store.
                                                                                                                                                                                                                                                                             
   - **Autobot Engine** — Multi-mode scanning (Sniper, DCA, limit orders, smart TP/SL exits). Real-time filters for age, volume, liquidity, and verification. Every loop logged: scan, checks, quote, swap.
   - **35 Intelligence Pillars** — Modular scoring and filtering system. Includes dev identity checker, smart money tracking, rug scanner, whale scanner, and more. Each pillar toggles independently, essentially a no-code ML trading strategy builder.                   
   - **Risk Engine** — Max daily loss limits, per-trade risk caps, V2 risk with regime awareness, portfolio bucket/category allocation. Institutional-grade risk management exposed through a consumer UI.
   - **Execution** — 1,200 concurrent transactions, 10ms monitoring, smart exit triggers. Multi-DEX routing across Solana.                                                                                                                                                   
   - **Seed Vault Integration** — Native on-device signing via Solana Seeker hardware. Private keys never leave the device.  



 ### [Solana Agent Wallet Adapter](https://github.com/mstevens843/solana-agent-wallet-adapter)

  Open-source signing layer for Solana AI agents. Agents request actions, the adapter prepares the signing request, and the user's real wallet approves. No env-var private keys, no embedded signer, no Phantom-only lock-in. Built for MCP, Wallet Standard, Vercel AI, and Solana Agent Kit.

  - Real-wallet approval layer: Routes agent signing through the wallet users already trust. Phantom, Backpack, Solflare, Glow, and other Wallet Standard providers fit the same browser path. The agent never touches the private key.
  - Multi-framework adapter architecture: One WalletBackend contract powers MCP tools, Vercel AI tools, and a Solana Agent Kit BaseWallet adapter. Framework integrations share the same signing protocol instead of each reinventing wallet approval.
  - MCP server for agent clients: Ships stdio and HTTP transports with tools for address lookup, message signing, transaction signing, sign-and-send, approval polling, and transaction simulation.
  - Wallet Standard web backend: Live browser backend for installed Solana wallets. Verified with Backpack on devnet for message signing, transaction signing, and sign-and-send broadcast.
  - Wallet compatibility fixes: Backpack routes through sign-then-RPC-send to avoid its native sign-and-send wallet failure. Phantom native sign-and-send receives minContextSlot, matching the known mobile workaround.
  - Polished browser demo: Demonstrates the full flow: agent plan approval with Phantom, wallet switch through Wallet Standard, Backpack message signing, devnet transaction creation, sign-only transaction, and sign-and-send broadcast.
  - Standards-first roadmap: Designed for Wallet Standard on web, MWA on Android, and wallet deeplinks on iOS. The browser path is live today, mobile-native backends are planned next.

  Apache-2.0. Open source. Public good infrastructure for non-custodial Solana agents.


  ### [iOS Solana Wallet Adapter (iWA)](https://github.com/mstevens843/ios-solana-wallet-adapter)

  Native Swift signing adapter for Solana iOS apps. Android has Mobile Wallet Adapter, web has Wallet Standard, but native iOS apps are still stuck hand-rolling Phantom, Solflare, and Backpack deeplinks or moving to WalletConnect / embedded custody.
  iWA gives iOS apps one URL/callback API for external wallet signing: the app keeps no private keys, the wallet shows approval, and the adapter handles encrypted requests and callbacks.

  - **Not MWA-for-iOS:** MWA is Android-only by protocol. iWA is the iOS-native counterpart built around universal links, wallet-specific deeplinks, and request/response callbacks.
  - **Multi-wallet Swift Package:** one `WalletAdapter` API across Phantom, Solflare, and Backpack for connect, sign message, sign transaction, sign all transactions, sign and send, and disconnect.
  - **Real encrypted wire layer:** CryptoKit X25519 ephemeral keys, TweetNaCl-compatible NaCl box encryption, Base58 wire encoding, nonce/session handling, encrypted callback decoding, and wallet error mapping.
  - **SwiftUI/UIKit lifecycle layer:** `SolanaWalletAdapterUI` turns fragile wallet URL bounces into async app calls with `.onOpenURL` routing, pending request cancellation, Keychain-backed state, and deterministic smoke-test logging.
  - **Wallet picker UX:** SwiftUI picker for Phantom, Solflare, Backpack, and Jupiter Mobile track, with Android-style **Just Once** / **Always** selection so native iOS apps can remember the user's preferred wallet.
  - **MWA-style app semantics on iOS transport:** `getCapabilities`, `signInWithSolana`, `authorize`, `deauthorize`, `signMessages`, `signTransactions`, and `signAndSendTransactions` aliases let iOS share the same app-level wallet vocabulary without
  falsely claiming MWA protocol support.
  - **Adds the missing iOS layer to the stack:** pairs with Android MWA work, web/agent Wallet Standard work, and game-engine SDKs so Solana apps can keep a consistent non-custodial signing model across web, agents, Android, iOS, Unity, Unreal, Godot,
  Cocos, and Capacitor.

  Apache-2.0. Public RC `0.2.0-rc.1`: local coverage and simulator mock flows are green; physical-iPhone wallet smoke logs are the remaining gate before stable production wording.


   ### [Cocos Creator MWA SDK for Solana](https://github.com/mstevens843/Cocos-Solana-MWA-SDK)
  
  **Built from scratch.** The first Solana Mobile Wallet Adapter 2.0 SDK for Cocos Creator. No prior SDK, no template, nothing to fork. Cocos powers 1.7M+ developers and dominates mobile games in Asia (40% of China's mobile titles, 60% of Korea's top 10, $5.56B WeChat mini-game economy). Until this SDK shipped, none of those developers could build on Solana
  
  - **Full MWA 2.0 parity:** authorize, SIWS, sign_messages (batch), sign_and_send_transactions, deauthorize, clone_authorization, getCapabilities, deleteAccount. Every method verified on real Solana Seeker hardware.
  - **Native Android bridge:** JsbBridge protocol over JSON, fresh LocalAssociationScenario per operation, ECDH + AES-GCM encryption, request-ID correlation, 60-second timeouts. Built directly against `clientlib-ktx 2.0.3`.
  - **Zero npm dependencies for the SDK core:** hand-rolled binary transaction serializer, Base58 codec, RPC client. Drop-in TypeScript module with no external runtime baggage. 
  - **Multi-wallet matrix:** Phantom, Solflare, Backpack, Jupiter, Seed Vault. All five hardware-verified end-to-end on Seeker.
  - **Persistent auth caching:** SQLite-backed token storage for silent reconnect across app restarts.
  - **Token Duel demo game:** bundled real-time portfolio-race game with an on-chain Anchor escrow program on devnet. Pick 3 tokens, stake SOL, settle via signAndSendTransaction. Proves the SDK drives real economic flows, not just wallet prompts.

    MIT-licensed. Open source. Public good infrastructure.    


  ### [Unreal Engine MWA SDK for Solana](https://github.com/mstevens843/unreal-solana-mwa)                                                                                                    
                                                                                                                                                                                              
  **The first production-ready Solana MWA plugin for Unreal Engine 5.** The community CaveWorld plugin (the only one Solana Mobile's docs link) hand-rolled the MWA wire protocol in C++, last
   commit June 2023, never shipped sign_messages, no LICENSE. This SDK wraps Solana Mobile's official Kotlin `clientlib-ktx` and exposes a thin C++ shim plus Blueprint surface — one to two  
  orders of magnitude less code, every protocol fix lands as a Maven version bump.                                                                                                            
                                                                                                                                                                                            
  - **Full MWA 2.0 parity:** authorize, reauthorize, deauthorize, sign_messages (batch + detached), sign_transactions, sign_and_send_transactions, SIWS 2.0, get_capabilities, deleteAccount. 
  Every method exposed as a Blueprint UFUNCTION with delegate, hardware-verified on Solana Seeker.                                                                                            
  - **Three-layer architecture:** Kotlin plugin driving `MobileWalletAdapter.transact { ... }`, C++ JNI bridge, UObject + UFunction Blueprint surface. UPL XML injects Maven deps, manifest 
  queries, GameActivity lifecycle hooks, and a foreground keep-alive service for the wallet round-trip.                                                                                       
  - **Three Sign And Send routes exposed per-call:** native MWA `sign_and_send_transactions`, sign-then-broadcast-via-app-RPC fallback (the path Backpack requires due to a                 
  `JsonDecodingException` crash in its native handler), or auto. Demo ships all three as side-by-side buttons so dApps can validate custom RPC submit, MEV-protection routes, or simulation   
  forwarding on every wallet.                                                                                                                                                               
  - **Multi-pubkey auth cache:** pluggable `ISolanaMWAAuthCache` interface, JSON-file default with one-time migration from the legacy single-record INI layout. Per-pubkey storage,           
  latest-pointer tracking, in-memory blacklist on Delete Account so reconnect doesn't auto-resurrect a just-deleted account.                                                                  
  - **Branded approval sheet:** `FSolanaIdentity::SDKDefault()` ships `Solana.Unreal-SDK` with the Solana Mobile favicon by default. dApps shipping their own brand call `MakeSolanaIdentity`
  Blueprint factory — wallets validate the URI host (Phantom Blowfish, Solflare origin check), so the URI is part of the trust UX.                                                            
  - **Multi-wallet matrix:** Phantom, Solflare, Backpack, Jupiter, Seed Vault — all five hardware-verified end-to-end on Seeker. Comprehensive `ESolanaWalletType` enum with IDs pinned to  
  wire-compat with Unity / Godot, plus `USolanaMWAUtils` helpers (base58/base64/hex codec, lamports↔SOL conversion, address shortening, transaction builder) and `USolanaMWAToast` JNI bridge.
                                                                                                                                                                                            
  MIT-licensed. Open source. The architectural twin is Virus-Axel's open-source Godot SDK — same wrap-the-Kotlin-clientlib pattern, adapted to Unreal's plugin model.     
                                                                                                                                                                                                                                                                              
   ### [Capacitor Solana Mobile Wallet Adapter](https://github.com/mstevens843/capacitor-solana-mobile-wallet-adapter)                                                                                                                                                       
   First Capacitor plugin for Solana Mobile Wallet Adapter. Open source.
                                                                                                                                                                                                                                                                              
   ### [Godot MWA SDK — Solana Mobile Grant](https://github.com/mstevens843/godot-solana-mwa-example)                                                                                                                                                                        
   Brought the Godot Mobile Wallet Adapter SDK to parity with the React Native SDK. Found and fixed 10 bugs in the SDK during integration, including signal reliability failures, type mismatches causing silent crashes, and stale key persistence after deauthorization. Submitted a clearState() SDK fix (PR #449) to enable proper disconnect/reconnect flows. Built a complete example app with multi-wallet support (Seed Vault, Phantom, Solflare, Backpack, Jupiter), verified on Solana Seeker hardware. All MWA flows working: connect, disconnect, reconnect fresh, reconnect cached, delete account, sign message.                                                                                                                                                
                                                            
   ### [Unity MWA SDK — Solana Mobile Grant](https://github.com/mstevens843/unity-solana-mwa-example)                                                                                                                                                                                                                                                                                                                                                                                                                                                     
   Brought the Unity Mobile Wallet Adapter SDK to parity with the React Native SDK. Found and fixed 11 bugs during hardware testing, including RPC cluster defaulting to DevNet blocking all non-Seed-Vault wallets, sign-in routing causing Phantom hangs, and Transaction.Serialize() NullRef on MWA accounts.
Implemented get_capabilities directly in the Solana.Unity-SDK source. a real MWA 2.0 method returning live wallet data from Phantom. Built extensible auth token caching, cache-only instant reconnect with lazy session init, and deterministic logging across all API methods. Complete example app with multi-wallet support (Seed Vault, Phantom, Solflare, Backpack, Jupiter) showcasing all MWA 2.0 APIs: authorize, reauthorize, deauthorize, sign_messages, sign_transactions, sign_and_send_transactions, get_capabilities, and wallet-confirmed account deletion. Verified on Solana Seeker hardware on
mainnet-beta.      
                                                                                                                                                                                                                                                                              
   ## What I Work With                                     
   React, Node.js, TypeScript, Vite, C#, GDScript, C++, Capacitor, Unity, Unreal Engine, Godot, Solana, Anchor                                                                                                                                                                              
                                                                                                                                                                                                                                                                              
   ## Links
   - [LinkedIn](https://www.linkedin.com/in/mathewbradleystevens)                                                                                                                                                                                                            
   - [Twitter](https://twitter.com/mattinfra) 
