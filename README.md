# Pool Party

**A networked, generative art experience on [Art Blocks](https://www.artblocks.io/collection/pool-party-by-basement-x-ryley-o) by BASEMENT x ryley-o.eth.**

Each mint purchases a randomly-selected ERC-20 token, then tracks its price over time through 12 automated Chainlink check-ins. These real-world price movements directly influence the artwork's visual output — making every piece a living, evolving composition.

> **Live site:** [https://pool-party.fun](https://pool-party.fun)
>
> The GitHub Pages deployment at `ryley-o.github.io/pool-party-site` redirects to the above. The original informational page source is kept in this repo for reference.

## How It Works

1. **Mint** — Collector chooses a price. 10% to Art Blocks, 10% to artists, 80% swapped into a random ERC-20 token via Uniswap V3.
2. **Live** — Chainlink Automation executes 12 price check-ins over the token's lifetime, injecting prices as PostParam values that shape the artwork.
3. **Withdraw** — After all check-ins complete, the collector can withdraw the underlying ERC-20 tokens to their wallet.

## Key Contracts

| Contract | Description |
|---|---|
| [StratHooks](https://github.com/ryley-o/StratHooks) | PostParam hook — mint logic, price check-ins, Chainlink Automation, withdrawal (UUPS upgradeable) |
| [GuardedEthTokenSwapper](https://github.com/ryley-o/GuardedEthTokenSwapper) | MEV-protected ETH→ERC20 swapper using Chainlink oracles and Uniswap V3 |
| [Art Blocks Contracts](https://github.com/ArtBlocks/artblocks-contracts) | Studio contract and PostMintParameter (PMP) system |

## Deployed Addresses (Ethereum Mainnet)

- **StratHooks Proxy:** [`0x9a3f4307b1d12aeA5E2633e6e10Fb3cf9Ac81F9a`](https://etherscan.io/address/0x9a3f4307b1d12aea5e2633e6e10fb3cf9ac81f9a)
- **GuardedEthTokenSwapper:** [`0x7FFc0E3F2aC6ba73ada2063D3Ad8c5aF554ED05f`](https://etherscan.io/address/0x7FFc0E3F2aC6ba73ada2063D3Ad8c5aF554ED05f)
- **Pool Party Studio Contract:** [`0xaa00b2b2db36b8f8004a9aa96f0012005d92b300`](https://etherscan.io/address/0xaa00b2b2db36b8f8004a9aa96f0012005d92b300)

## Development

This is a static single-page site deployed via GitHub Pages. To preview locally:

```bash
python3 -m http.server 8080
# then open http://localhost:8080
```

Deployment is automatic on push to `main` via the [GitHub Actions workflow](.github/workflows/deploy.yml).
