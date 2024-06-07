# Project: Create a Token

## Overview

The `MyEdge` smart contract is a simple token deployed on the local blockchain. It includes the following features:

- Public variables for token details such as name, abbreviation, and total supply.
- A mapping to track balances of addresses.
- Functions to mint and burn tokens with appropriate checks.

## Contract Details

### Public Variables

- `string public tokenName = "EDGE";`
- `string public tokenAbbrv = "EDG";`
- `uint256 public totalSupply = 0;`
- `uint256 public constant MAX_SUPPLY = 5000;`

### Mapping

- `mapping(address => uint) public balances;`

### Functions

#### Mint Function

##
        function mint(address _to, uint _value) public {
        require(totalSupply + _value <= MAX_SUPPLY, "Exceeds maximum supply of 5000");
        totalSupply += _value;
        balances[_to] += _value;
        }

#### Burn Function

##
        function burn(address _from, uint _value) public {
        require(balances[_from] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_from] -= _value;
        }

### Usage

#### Minting Tokens:
##
        mint(address recipient, uint amount);

#### Burning Tokens:
##
        burn(address sender, uint amount);