# IntercomRoulette Skill

## Overview
IntercomRoulette is a decentralized P2P roulette game built on Intercom (Trac Network). This skill file describes how agents can interact with the game.

## Agent Capabilities

### 1. Start a Game Session
Agents can initiate a roulette room by opening an Intercom sidechannel:
```
ACTION: start_roulette_session
PARAMS: { room_id: "<unique_id>", host: "<trac_address>" }
RESPONSE: { session_id, join_code }
```

### 2. Place a Bet
```
ACTION: place_bet
PARAMS: {
  session_id: "<id>",
  player: "<trac_address>",
  bet_type: "color" | "number" | "range",
  bet_value: "red" | "black" | 0-36 | "1-18" | "19-36",
  amount: <number>
}
RESPONSE: { bet_id, confirmed: true/false }
```

### 3. Spin the Wheel
Only the host agent can trigger a spin:
```
ACTION: spin_wheel
PARAMS: { session_id: "<id>", host: "<trac_address>" }
RESPONSE: { result: <0-36>, color: "red"|"black"|"green", winners: [...] }
```

### 4. Get Session State
```
ACTION: get_session_state
PARAMS: { session_id: "<id>" }
RESPONSE: { players, bets, last_result, history }
```

### 5. Broadcast Result
After spin, result is broadcast to all connected peers via Intercom sidechannel automatically.

## State Schema (Replicated State Layer)
```json
{
  "session_id": "string",
  "host": "trac_address",
  "players": ["trac_address"],
  "bets": [
    { "player": "trac_address", "type": "color", "value": "red", "amount": 10 }
  ],
  "spins": [
    { "result": 17, "color": "black", "timestamp": 1700000000 }
  ]
}
```

## Rules
- Minimum bet: 1 TNK
- House edge: 0% (fair P2P game)
- Max players per session: 10
- Spin is triggered by host after all bets are placed

## Integration with Intercom
This app uses:
- **Sidechannels**: Real-time bet coordination between players
- **Replicated State**: Persistent game history and results
- **Trac Address**: Player identity and payout recipient
