# x402 Paywall Skill

Production x402 (HTTP 402) paywall for monetizing any API/agent skill.

## Files
- `SKILL.md` — SkillShop manifest ($19, USDC on Base)
- `api/index.py` — Flask paywall endpoint
- `requirements.txt` — Python deps
- `vercel.json` — Vercel serverless config

## Deploy
```bash
vercel --prod
# Set PAY_TO, X402_NETWORK, PRICE env vars
```

## Live
https://x402-paywall-bgl2ek1ck-solmount.vercel.app