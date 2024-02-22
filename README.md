# Cytoswap Swap Router

This repository contains smart contracts for swapping on the Cytoswap V3 protocols.

## Bug bounty

This repository is subject to the Cytoswap V3 bug bounty program,
per the terms defined [here](./bug-bounty.md).

## Local deployment

In order to deploy this code to a local testnet, you should install the npm package
`@cytoswap/swap-router-contracts`
and import bytecode imported from artifacts located at
`@cytoswap/swap-router-contracts/artifacts/contracts/*/*.json`.
For example:

```typescript
import {
  abi as SWAP_ROUTER_ABI,
  bytecode as SWAP_ROUTER_BYTECODE,
} from '@cytoswap/swap-router-contracts/artifacts/contracts/SwapRouter02.sol/SwapRouter02.json'

// deploy the bytecode
```

This will ensure that you are testing against the same bytecode that is deployed to
mainnet and public testnets, and all Cytoswap code will correctly interoperate with
your local deployment.

## Using solidity interfaces

The swap router contract interfaces are available for import into solidity smart contracts
via the npm artifact `@cytoswap/swap-router-contracts`, e.g.:

```solidity
import '@cytoswap/swap-router-contracts/contracts/interfaces/ISwapRouter02.sol';

contract MyContract {
  ISwapRouter02 router;

  function doSomethingWithSwapRouter() {
    // router.exactInput(...);
  }
}

```

## Tests

Some tests use Hardhat mainnet forking and therefore require an archive node.
Either create a `.env` file in the workspace root containing:

```
ARCHIVE_RPC_URL='...'
```

Or set the variable when running tests:

```
export ARCHIVE_RPC_URL='...' && npm run test
```
