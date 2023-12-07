# Coupon Token (CT) Smart Contract

## Overview

The Coupon Token (CT) smart contract is an Ethereum-based ERC-20 token that extends the functionality of the OpenZeppelin ERC20 standard and incorporates ownership management through the Ownable contract. This token allows for minting, burning, and transferring of tokens, with specific access controls to ensure that only the owner can perform certain operations.

## Features

1. **Minting:** Only the owner of the contract can create new tokens by calling the `mint` function. This function requires specifying a recipient address (cashier) and the amount of tokens to be created.

```solidity
function mint(address cashier, uint256 numeral) external onlyOwnerCanMint {
    // Implementation details
}
```

2. **Burning:** Token holders can burn their own tokens by calling the `burn` function. This operation requires specifying the amount of tokens to be burned, and the caller must have sufficient funds.

```solidity
function burn(uint256 numeral) external {
    // Implementation details
}
```

3. **Transferring:** The standard ERC-20 `transfer` function is overridden to add additional checks. Transfers are only allowed if the specified recipient is a valid address, the transferred amount is positive, and the sender has sufficient funds.

```solidity
function transfer(address cashier, uint256 numeral) public override returns (bool) {
    // Implementation details
}
```

4. **Access Controls:** The `onlyOwnerCanMint` modifier ensures that only the owner can mint new tokens, adding an extra layer of security.

```solidity
modifier onlyOwnerCanMint() {
    require(isOwner(), "Only the owner can create new tokens");
    _;
}
```

## Deployment

The contract is deployed with the name "Coupon Token" and the symbol "CT". The constructor sets the contract owner to the address that deploys the contract.

```solidity
constructor() ERC20("Coupon Token", "CT") Ownable(msg.sender) {}
```

## Internal Functions

- **availableFunds:** Internal function that returns the balance of tokens for a given account.

```solidity
function availableFunds(address account) internal view returns (uint256) {
    // Implementation details
}
```

- **isOwner:** Internal function that checks if the caller is the owner of the contract.

```solidity
function isOwner() internal view returns (bool) {
    // Implementation details
}
```

## Author 

Vignesh

s82167500@gmail.com
