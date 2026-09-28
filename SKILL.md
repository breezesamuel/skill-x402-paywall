---
name: "x402 HTTP 402 Paywall for APIs & Agents"
description: "Drop-in x402 paywall for any HTTP endpoint. Returns 402 Payment Required with USDC requirements, verifies payments via x402 facilitator. Live on Vercel, testnet-ready, mainnet-switchable."
version: "1.0.0"
price: "19.00 USD"
wallet_address: "0x12A2b19eFA9D8BC48ac156Cc8FdfC7cC0Dff36aB"
category: "payments"
tags: ["x402", "http402", "usdc", "base", "vercel", "flask", "agents"]
author: "breezesamuel"
license: "MIT"
repository: "https://github.com/breezesamuel/skill-x402-paywall"
documentation: "https://github.com/breezesamuel/skill-x402-paywall/blob/main/README.md"
---
# x402 HTTP 402 Paywall

## Overview
Turn any API/tool/agent skill into a pay-per-call endpoint in <50 lines. Uses the x402 protocol (HTTP 402 Payment Required) with USDC on Base-Sepolia testnet.

## Features
- **Zero-config x402**: `x402ResourceServer` + `ExactEvmServerScheme`
- **Live on Vercel**: Serverless Flask, auto-scales, zero cold-start issues
- **USDC Payments**: $0.10/call on Base-Sepolia (testnet), mainnet switchable via env
- **Agent-ready**: Returns machine-readable payment requirements, compatible with x402 facilitator
- **Verified 402 Flow**: `GET /pay/today` → 402 + requirements → pay → verify → 200

## Quick Start
```bash
# Deploy to Vercel
vercel --prod

# Set env
PAY_TO=your_wallet_address
X402_NETWORK=eip155:84532  # Base-Sepolia
PRICE=0.10 USD
```

## Live Demo
```
curl -i https://x402-paywall-bgl2ek1ck-solmount.vercel.app/pay/today
# → HTTP/1.1 402 Payment Required
# → {"requirements":[{"scheme":"exact","network":"eip155:84532","asset":"0x036C...","amount":"100000","pay_to":"0x12A2..."}]}
```

## Integration
```python
# Client pays via x402 facilitator
from x402.http import HTTPFacilitatorClient
from x402.mechanisms.evm.exact import ExactEvmServerScheme

facilitator = HTTPFacilitatorClient()
server = x402ResourceServer(facilitator)
server.register("eip155:84532", ExactEvmServerScheme())
# ... verify payment payload from client ...
```

## Revenue Proof
Live at `https://x402-paywall-bgl2ek1ck-solmount.vercel.app` — listed on awesome-x402-servers (PR #76), indexed by the402.dev.

## Support
Issues: https://github.com/breezesamuel/skill-x402-paywall/issues