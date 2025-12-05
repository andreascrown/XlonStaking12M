XLON Staking Pool Demo — README
================================

Overview
--------
This demo showcases a 12‑month fixed‑term staking pool built for the XLON blockchain.
Users stake native XLON and receive a fixed, prefunded reward after the 12‑month lock period.
The demo runs in Remix and demonstrates the core staking logic that can serve as the first DeFi module on XLON.

Key Features
------------
• Native XLON staking via stake() function.
• Supports simple UX via direct transfer (receive()).
• Fixed reward model calculated at stake time.
• Rewards must be prefunded (no minting).
• 12‑month lock of principal and reward.
• Claim principal + reward after maturity.
• Uses Ownable, Pausable, ReentrancyGuard for security.
• Clear event logging.

Contract Functions (Scope of Demo)
----------------------------------
Admin Functions:
• depositRewards() — Owner funds reward pool.
• setRateBps() — Update reward rate.
• pause() / unpause() — Emergency stop.

User Functions:
• stake() — User stakes XLON (send value). **Used in the demo**.
• claim() — Withdraw principal + reward after lock period.
• positionOf(address) — View staking info.
• timeToUnlock(address) — See remaining lock time.

Demo Instructions (Remix)
-------------------------
1. Setup:
   • Open https://remix.ethereum.org
   • Create file: XlonStaking12M.sol
   • Paste contract code
   • Compile with Solidity 0.8.20

2. Deploy:
   • Environment: JavaScript VM (Shanghai)
   • Constructor: 800 (8% reward rate)
   • Deploy

3. Prefund Reward Pool:
   • Select owner account
   • Set Value = 5 ether
   • Call depositRewards()

4. Stake (Demo Focus):
   • Switch to a second account
   • Set Value = 1 ether
   • Call stake()
   • Call positionOf(account)

5. Claim (Explanation Only):
   • Needs block.timestamp ≥ unlockTime
   • User calls claim() to receive principal + reward.

