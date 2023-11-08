---
title: PriceSubmitter
---

<!-- This is an autogenerated file. Do not edit! -->

# `PriceSubmitter` { #ct_pricesubmitter }

<div class="api-node-source" markdown>
[Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol) | Inherits from [IIPriceSubmitter](./IIPriceSubmitter.md), [GovernedAtGenesis](./GovernedAtGenesis.md), [AddressUpdatable](./AddressUpdatable.md)
</div>

<div class="api-node-internal" markdown>

Receives prices from [FTSO data providers](https://docs.flare.network/tech/ftso).

It then forwards the submissions to the appropriate FTSO contract,
allowing data providers to perform all required operations in a single transaction
per price epoch.

</div>

<div class="api-node-type" markdown>

## Functions

<div class="api-node" markdown>

### `cancelGovernanceCall` { #fn_cancelgovernancecall_67fc4029 }

<div class="api-node-source" markdown>
Defined in `GovernedBase` ([Docs](./GovernedBase.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/governance/implementation/GovernedBase.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function cancelGovernanceCall(
    bytes4 _selector
) external;
```

Cancel a timelocked [`governance`](#fn_governance_5aa6e675) call before it has been executed.

Only [`governance`](#fn_governance_5aa6e675) can call this method.

| Parameters | Type | Description |
| ---------- | ---- | ----------- |
| `_selector` | `bytes4` | The method selector. |

</div>
</div>

<div class="api-node" markdown>

### `constructor` { #fn_constructor_undefined }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
constructor(
) public;
```

This [`constructor`](#fn_constructor_undefined) should contain no code as this contract is pre-loaded into the genesis block.
  The super constructors are called for testing convenience.

</div>
</div>

<div class="api-node" markdown>

### `executeGovernanceCall` { #fn_executegovernancecall_5ff27079 }

<div class="api-node-source" markdown>
Defined in `GovernedBase` ([Docs](./GovernedBase.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/governance/implementation/GovernedBase.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function executeGovernanceCall(
    bytes4 _selector
) external;
```

Execute the timelocked [`governance`](#fn_governance_5aa6e675) calls once the timelock period expires.

Only executor can call this method.

| Parameters | Type | Description |
| ---------- | ---- | ----------- |
| `_selector` | `bytes4` | The method selector (only one timelocked call per method is stored). |

</div>
</div>

<div class="api-node" markdown>

### `getAddressUpdater` { #fn_getaddressupdater_5267a15d }

<div class="api-node-source" markdown>
Defined in `AddressUpdatable` ([Docs](./AddressUpdatable.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/addressUpdater/implementation/AddressUpdatable.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function getAddressUpdater(
) public view returns (
    address _addressUpdater);
```

Returns the configured address updater.

| Returns | Type | Description |
| ------- | ---- | ----------- |
| `_addressUpdater` | `address` | The `AddresUpdater` contract that can update our contract address list, as a response to a governance call. |
</div>
</div>

<div class="api-node" markdown>

### `getCurrentRandom` { #fn_getcurrentrandom_d89601fd }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function getCurrentRandom(
) external view returns (
    uint256);
```

Returns the random number for the previous epoch, obtained from the random numbers
provided by all data providers along with their data submissions.
Note that the random number for the previous epoch keeps updating as new submissions are revealed.

It never reverts.

| Returns | Type | Description |
| ------- | ---- | ----------- |
| [0] | `uint256` | Random number calculated from all data provider's submissions. |
</div>
</div>

<div class="api-node" markdown>

### `getFtsoManager` { #fn_getftsomanager_b39c6858 }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function getFtsoManager(
) external view returns (
    contract IFtsoManagerGenesis);
```

Returns the address of the [`FtsoManager`](./FtsoManager.md) contract.

</div>
</div>

<div class="api-node" markdown>

### `getFtsoRegistry` { #fn_getftsoregistry_8c9d28b6 }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function getFtsoRegistry(
) external view returns (
    contract IFtsoRegistryGenesis);
```

Returns the address of the [`FtsoRegistry`](./FtsoRegistry.md) contract.

</div>
</div>

<div class="api-node" markdown>

### `getRandom` { #fn_getrandom_cd4b6914 }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function getRandom(
    uint256 _epochId
) external view returns (
    uint256);
```

Returns the random number used in a specific past epoch, obtained from the random numbers
provided by all data providers along with their data submissions.

| Parameters | Type | Description |
| ---------- | ---- | ----------- |
| `_epochId` | `uint256` | ID of the queried epoch. Current epoch cannot be queried, and the previous epoch is constantly updated as data providers reveal their prices and random numbers. Note that only the last 50 epochs can be queried and there is no bounds checking for this parameter. Out-of-bounds queries return undefined values. |

| Returns | Type | Description |
| ------- | ---- | ----------- |
| [0] | `uint256` | The random number used in that epoch. |
</div>
</div>

<div class="api-node" markdown>

### `getTrustedAddresses` { #fn_gettrustedaddresses_ffacb84e }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function getTrustedAddresses(
) external view returns (
    address[]);
```

Returns the list of trusted addresses that are always allowed to submit and reveal.

| Returns | Type | Description |
| ------- | ---- | ----------- |
| [0] | `address[]` | address[] Array of trusted voter addresses. |
</div>
</div>

<div class="api-node" markdown>

### `getVoterWhitelister` { #fn_getvoterwhitelister_71e1fad9 }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function getVoterWhitelister(
) external view returns (
    address);
```

Returns the address of the [`VoterWhitelister`](./VoterWhitelister.md) contract managing the data provider whitelist.

</div>
</div>

<div class="api-node" markdown>

### `governance` { #fn_governance_5aa6e675 }

<div class="api-node-source" markdown>
Defined in `GovernedBase` ([Docs](./GovernedBase.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/governance/implementation/GovernedBase.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function governance(
) public view returns (
    address);
```

Returns the current effective [`governance`](#fn_governance_5aa6e675) address.

</div>
</div>

<div class="api-node" markdown>

### `initialise` { #fn_initialise_9d6a890f }

<div class="api-node-source" markdown>
Defined in `GovernedAtGenesis` ([Docs](./GovernedAtGenesis.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/governance/implementation/GovernedAtGenesis.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function initialise(
    address _governance
) public pure;
```

Disallow [`initialise`](#fn_initialise_9d6a890f) to be called.

| Parameters | Type | Description |
| ---------- | ---- | ----------- |
| `_governance` | `address` | The governance address for initial claiming. |

</div>
</div>

<div class="api-node" markdown>

### `revealPrices` { #fn_revealprices_e2db5a52 }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function revealPrices(
    uint256 _epochId,
    uint256[] _ftsoIndices,
    uint256[] _prices,
    uint256 _random
) external;
```

Reveals submitted prices during the epoch reveal period.
The hash of FTSO indices, prices, random number, and voter address must be equal
to the hash previously submitted with [`submitHash`](#fn_submithash_8fc6f667).
Emits a [`PricesRevealed`](#ev_pricesrevealed) event.

| Parameters | Type | Description |
| ---------- | ---- | ----------- |
| `_epochId` | `uint256` | ID of the epoch to which the price hashes are submitted. |
| `_ftsoIndices` | `uint256[]` | List of FTSO indices in ascending order. |
| `_prices` | `uint256[]` | List of submitted prices in USD. |
| `_random` | `uint256` | Submitted random number. |

</div>
</div>

<div class="api-node" markdown>

### `setAddressUpdater` { #fn_setaddressupdater_aea36b53 }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function setAddressUpdater(
    address _addressUpdater
) external;
```

Sets the address updater contract.
Only [`governance`](#fn_governance_5aa6e675) cal call this method.

| Parameters | Type | Description |
| ---------- | ---- | ----------- |
| `_addressUpdater` | `address` | Address of the [`AddressUpdater`](./AddressUpdater.md) contract. |

</div>
</div>

<div class="api-node" markdown>

### `setTrustedAddresses` { #fn_settrustedaddresses_9ec2b581 }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function setTrustedAddresses(
    address[] _trustedAddresses
) external;
```

Set the trusted addresses that are always allowed to submit and reveal.
Trusted addresses are used, for example, in fallback mode.
Only FTSO Manager can call this method.

| Parameters | Type | Description |
| ---------- | ---- | ----------- |
| `_trustedAddresses` | `address[]` | Array of FTSO data provider addresses (voters). The previous list of trusted addresses is discarded. |

</div>
</div>

<div class="api-node" markdown>

### `submitHash` { #fn_submithash_8fc6f667 }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function submitHash(
    uint256 _epochId,
    bytes32 _hash
) external;
```

Submits a hash for the current epoch. Can only be called by FTSO data providers
whitelisted through the `VoterWhitelisted` contract.
Emits the [`HashSubmitted`](#ev_hashsubmitted) event.

| Parameters | Type | Description |
| ---------- | ---- | ----------- |
| `_epochId` | `uint256` | ID of the target epoch to which the hash is submitted. |
| `_hash` | `bytes32` | A hash of the FTSO indices, prices, random number, and voter address. |

</div>
</div>

<div class="api-node" markdown>

### `switchToProductionMode` { #fn_switchtoproductionmode_f5a98383 }

<div class="api-node-source" markdown>
Defined in `GovernedBase` ([Docs](./GovernedBase.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/governance/implementation/GovernedBase.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function switchToProductionMode(
) external;
```

Enter the production mode after all the initial [`governance`](#fn_governance_5aa6e675) settings have been set.
This enables timelocks and the [`governance`](#fn_governance_5aa6e675) can be obtained afterward by calling
[`governanceSettings`](#va_governancesettings).getGovernanceAddress().
Emits [`GovernedProductionModeEntered`](#ev_governedproductionmodeentered).

</div>
</div>

<div class="api-node" markdown>

### `updateContractAddresses` { #fn_updatecontractaddresses_b00c0b76 }

<div class="api-node-source" markdown>
Defined in `AddressUpdatable` ([Docs](./AddressUpdatable.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/addressUpdater/implementation/AddressUpdatable.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function updateContractAddresses(
    bytes32[] _contractNameHashes,
    address[] _contractAddresses
) external;
```

External method called from [`AddressUpdater`](./AddressUpdater.md) only.

</div>
</div>

<div class="api-node" markdown>

### `voterWhitelistBitmap` { #fn_voterwhitelistbitmap_7ac420ad }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function voterWhitelistBitmap(
    address _voter
) external view returns (
    uint256);
```

Returns a bitmap of all FTSOs for which a data provider is allowed to submit prices or hashes.

| Parameters | Type | Description |
| ---------- | ---- | ----------- |
| `_voter` | `address` | Address of the voter. |

| Returns | Type | Description |
| ------- | ---- | ----------- |
| [0] | `uint256` | If a data provider is allowed to vote for a given FTSO index, the corresponding bit in the result is 1. |
</div>
</div>

<div class="api-node" markdown>

### `voterWhitelisted` { #fn_voterwhitelisted_9d986f91 }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function voterWhitelisted(
    address _voter,
    uint256 _ftsoIndex
) external;
```

Called from the [`VoterWhitelister`](./VoterWhitelister.md) contract when a new voter has been whitelisted.

Only the [`VoterWhitelister`](./VoterWhitelister.md) contract can call this method.

| Parameters | Type | Description |
| ---------- | ---- | ----------- |
| `_voter` | `address` | Voter address that has been added to the whitelist. |
| `_ftsoIndex` | `uint256` | Index of the FTSO to which the voter has registered. Each FTSO has its own whitelist. |

</div>
</div>

<div class="api-node" markdown>

### `votersRemovedFromWhitelist` { #fn_votersremovedfromwhitelist_76794efb }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
function votersRemovedFromWhitelist(
    address[] _removedVoters,
    uint256 _ftsoIndex
) external;
```

Called from the [`VoterWhitelister`](./VoterWhitelister.md) contract when one or more voters have been removed.

Only the [`VoterWhitelister`](./VoterWhitelister.md) contract can call this method.

| Parameters | Type | Description |
| ---------- | ---- | ----------- |
| `_removedVoters` | `address[]` |  |
| `_ftsoIndex` | `uint256` | Index of the FTSO to which the voters were registered. Each FTSO has its own whitelist. |

</div>
</div>

</div>

<div class="api-node-type" markdown>

## Modifiers

<div class="api-node" markdown>

### `onlyAddressUpdater` { #md_onlyaddressupdater }

<div class="api-node-source" markdown>
Defined in `AddressUpdatable` ([Docs](./AddressUpdatable.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/addressUpdater/implementation/AddressUpdatable.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
modifier onlyAddressUpdater()
```

Only the `AdressUpdater` contract can call this method.
Its address is set at construction time but it can also update itself.

</div>
</div>

<div class="api-node" markdown>

### `onlyFtsoManager` { #md_onlyftsomanager }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
modifier onlyFtsoManager()
```

Only the `ftsoManager` can call this method.

</div>
</div>

<div class="api-node" markdown>

### `onlyGovernance` { #md_onlygovernance }

<div class="api-node-source" markdown>
Defined in `GovernedBase` ([Docs](./GovernedBase.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/governance/implementation/GovernedBase.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
modifier onlyGovernance()
```

</div>
</div>

<div class="api-node" markdown>

### `onlyImmediateGovernance` { #md_onlyimmediategovernance }

<div class="api-node-source" markdown>
Defined in `GovernedBase` ([Docs](./GovernedBase.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/governance/implementation/GovernedBase.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
modifier onlyImmediateGovernance()
```

</div>
</div>

<div class="api-node" markdown>

### `onlyWhitelister` { #md_onlywhitelister }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
modifier onlyWhitelister()
```

Only the `voterWhitelister` can call this method.

</div>
</div>

</div>

<div class="api-node-type" markdown>

## Variables

<div class="api-node" markdown>

### `MINIMAL_RANDOM` { #va_minimal_random }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
    uint256 MINIMAL_RANDOM
```

Minimal random value accepted along price submissions.
Submitted random values below this threshold will revert.

</div>
</div>

<div class="api-node" markdown>

### `RANDOM_EPOCH_CYCLIC_BUFFER_SIZE` { #va_random_epoch_cyclic_buffer_size }

<div class="api-node-source" markdown>
Defined in `PriceSubmitter` ([Docs](./PriceSubmitter.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/genesis/implementation/PriceSubmitter.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
    uint256 RANDOM_EPOCH_CYCLIC_BUFFER_SIZE
```

Number of past random numbers remembered.

</div>
</div>

<div class="api-node" markdown>

### `governanceSettings` { #va_governancesettings }

<div class="api-node-source" markdown>
Defined in `GovernedBase` ([Docs](./GovernedBase.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/governance/implementation/GovernedBase.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
    contract IGovernanceSettings governanceSettings
```

Governance Settings.

</div>
</div>

<div class="api-node" markdown>

### `productionMode` { #va_productionmode }

<div class="api-node-source" markdown>
Defined in `GovernedBase` ([Docs](./GovernedBase.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/governance/implementation/GovernedBase.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
    bool productionMode
```

When true, [`governance`](#fn_governance_5aa6e675) is enabled and cannot be disabled. See [`switchToProductionMode`](#fn_switchtoproductionmode_f5a98383).

</div>
</div>

<div class="api-node" markdown>

### `timelockedCalls` { #va_timelockedcalls }

<div class="api-node-source" markdown>
Defined in `GovernedBase` ([Docs](./GovernedBase.md), [Source](https://gitlab.com/flarenetwork/flare-smart-contracts/-/tree/master/contracts/governance/implementation/GovernedBase.sol)).
</div>

<div class="api-node-internal" markdown>

```solidity
    mapping(bytes4 => struct GovernedBase.TimelockedCall) timelockedCalls
```

List of pending timelocked [`governance`](#fn_governance_5aa6e675) calls.

</div>
</div>

</div>
