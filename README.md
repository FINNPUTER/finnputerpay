# FinnputerPay

Non-custodial payment links for **$FINNPUTER** on Solana.

Live at: https://finnputerpay.xyz (pending domain purchase + DNS)

## What it is

A zero-sign-up payment link generator for the FINNPUTER creator token launched on Bags.fm. Creators paste in their wallet address + an amount, get a shareable link with a QR code. Fans tap the link → Phantom opens → pay in $FINNPUTER → done.

## Stack

- Static HTML/CSS/JS — no backend, no database, no sign-up
- Hosted on GitHub Pages + custom domain
- Uses **Solana Pay** URL standard for wallet deep-linking
- Live price via **DexScreener API**
- QR codes via `qrcodejs`

## Token

- **Name:** FINNPUTER
- **Chain:** Solana
- **Mint:** `Xp8dC5i7EcAeZo873ijwvipt3pUbgvgi5sHsg9sBAGS`
- **Launched via:** [Bags.fm](https://bags.fm)

## Structure

```
/
├── index.html            Landing page + payment link generator
├── pay/
│   └── index.html        Checkout page (Solana Pay integration)
├── logo.png              FINNPUTER CRT icon
├── favicon.png
├── apple-touch-icon.png
├── og-image.png          1200×630 social preview
└── README.md
```

## How it works

1. **Creator** opens `finnputerpay.xyz`, enters amount + wallet address, clicks Generate
2. Browser builds URL like `https://finnputerpay.xyz/pay/?to=WALLET&amount=10&cur=USD&d=Note`
3. **Fan** taps the link
4. Checkout page fetches live FINNPUTER price, computes token amount, shows details
5. Fan clicks "Pay with Phantom" → browser fires `solana:WALLET?amount=X&spl-token=MINT` URL scheme
6. Phantom extension (desktop) or app (mobile) intercepts, pre-fills, fan approves
7. Done — on-chain SPL token transfer, non-custodial

## License

Personal project. Not affiliated with Anthropic or Bags.fm.
