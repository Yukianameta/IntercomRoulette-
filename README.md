# 🎡 IntercomRoulette

A decentralized, peer-to-peer roulette game built on top of [Intercom](https://github.com/Trac-Systems/intercom) — the Trac Network P2P agent stack.

Players connect via Intercom sidechannels to place bets, spin the wheel, and settle results — all without a central server.

<img width="1278" height="852" alt="image" src="https://github.com/user-attachments/assets/aa521ad3-c226-4984-b04c-1390ff9be99e" />

## 🎮 How It Works

- Players open an Intercom sidechannel session
- Each player places a bet (color, number, or range)
- The host spins the wheel — result is broadcast via Intercom P2P to all participants
- Winners are announced and logged to the shared replicated-state layer
- All bet history is stored on-chain via Intercom's durable state

## 🚀 Features

- 🎰 Classic European Roulette (0–36)
- 🟥🟩 Red/Black, Odd/Even, Number betting
- 👥 Multiplayer via Intercom P2P sidechannels
- 📜 Bet history logged to shared state
- 🌐 Fully browser-based `index.html` — no install needed
- 🤖 Agent-compatible skill file included

## 🛠️ Quick Start

```bash
git clone https://github.com/YOUR_USERNAME/IntercomRoulette
cd IntercomRoulette
# Open index.html in your browser
open index.html
```

Or just open `index.html` directly in any modern browser.

## 📸 Screenshots

> Game UI screenshot and gameplay demo video available in `/docs/screenshots/`

## 💰 Trac Address

**Trac Address (for TNK payout):**
```
trac1k0zrnehdd9nkl4cgrfk6t5vf2gkhpx43te0fp6f6crmpaxr370qqff840t
```

## 🔗 Links

- Upstream: https://github.com/Trac-Systems/intercom
- Awesome Intercom: https://github.com/Trac-Systems/awesome-intercom

## 📄 License

MIT
