# $REAPING Flywheel

How creator rewards become movie tickets and burns. Everything below is verifiable on-chain.

## The split

Every $REAPING trade pays a 0.30% creator fee into a creator vault. That fee is split three ways by an on-chain SharingConfig:

| Share | Wallet | Purpose |
|-------|--------|---------|
| 50% | `HLg5pzxU6D2Vvk8hACCJCVk9VnoBb22MecrmFYLYCust` | Movie tickets |
| 25% | `DCLtQuhMJCSbc9GSSAE7zYwDjm7nmQssy92hYWdLJS7x` | Burns |
| 25% | `9gT17ULqTMcPCEf9rHavAfn9kxBmdb7wNso28Ldyd49D` (AbackSaberMiner) | Creator keep |

The split is set once and then locked on-chain — no one, including the creator, can change it after setup. Anyone can read the config and verify the percentages.

## Movie tickets (50%)

- When the tickets wallet accumulates enough SOL for a ticket (threshold: $25 — one AMC ticket, proposed), an AMC Theatres gift card is bought with SOL via Coinsbee.
- AMC gift cards are US-only, so winners need to be able to use AMC in the United States.
- A winner is picked at random from a snapshot of $REAPING holders, taken at a random, unannounced time so nobody can buy in just before the draw. To be eligible you must hold at least **$20 of $REAPING** at snapshot time. The snapshot excludes the bonding curve and pool accounts, the burn wallet and the creator wallet.
- **Larger holders:** entries follow a curve, not a straight line — **every doubling of your holdings adds one entry, with no cap**. $20 gets 1 entry, $40 gets 2, $80 gets 3, $160 gets 4, $320 gets 5, and so on. So a $100 holder gets 3 entries and a $200 holder gets 4, and holding more always earns more entries — each extra one just costs double the last. Bigger holders get better odds, but the curve flattens fast so nobody can buy the whole draw.
- The code is delivered privately (X DM), and a dust SOL transfer with a memo is sent to the winner's wallet as public proof the ticket was given out. The transaction is posted so anyone can verify it on Solscan.
- More trading = more tickets given out.

## Burns (25%)

- When the burns wallet accumulates enough SOL (threshold proposed: $10), it swaps SOL for $REAPING and sends the tokens to the Solana incinerator (`1nc1nerator11111111111111111111111111111111`), where they can never be recovered.
- Every burn transaction is posted so anyone can verify it on Solscan.
- More trading = more supply burned.

## How to verify

- Watch the three wallets above on Solscan: rewards landing, tickets being bought, burns going out.
- Every ticket giveaway and every burn is posted with its transaction signature.
- The split itself is readable on-chain in the coin's SharingConfig.

## What is NOT in this repo

The automation script, wallet private keys, and gift-card API credentials are deliberately not here. Keys and credentials are never published. Only the mechanism and the public addresses are documented.
