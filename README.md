# MarinoContract

## Description

This repository contains a Solidity smart contract named `MyContract`. The contract is written in Solidity version 0.8.25 and is licensed under the MIT license.

The contract implements the `require()`, `assert()`, and `revert()` statements, which are fundamental to error handling in Solidity.

## Features

- **Mapping Variable**: The contract includes a mapping variable `balances` that stores the balance of each address.

- **Deposit Function**: The `deposit` function allows an address to deposit a certain value into their account. The function requires that the deposit value be greater than 100. If the balance after depositing is less than the deposit value, the function reverts the transaction.

- **Withdraw Function**: The `withdraw` function allows an address to withdraw a certain value from their account. The function requires that the balance of the address be greater than or equal to the withdrawal value. If the balance after withdrawing is less than 0, the function reverts the transaction.

## EXECUTING PROGRAM 

To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., HelloWorld.sol). Copy and paste the following code into the file:

// SPDX-License-Identifier: MIT
pragma solidity 0.8.25;

//Write a smart contract that implements the require(), assert() and revert() statements.

contract MarinoContract {

    // Mapping variable to store balances
    mapping(address => uint) public balances;

    // Deposit Function
    function deposit(address _address, uint _value) public {
        require(_value > 100, "Deposit value must be greater than 100");

        balances[_address] += _value;

        assert(balances[_address] >= _value);
        if (balances[_address] < _value) {
            revert("Deposit failed");
        }
    }

    // Withdraw Function
    function withdraw(address _address, uint _value) public {
        require(balances[_address] >= _value, "Insufficient balance");

        balances[_address] -= _value;

        assert(balances[_address] >= 0);
        if (balances[_address] < 0) {
            revert("Withdrawal failed");
        }
    }
}


## Usage

To interact with this contract, you can use a web3 provider like Metamask and a frontend JavaScript library like web3.js or ethers.js.

## Author

Marino, Chloe Andrei BS INFORMATION TECHNNOLOGY 3.2  https://academy.metacrafters.io/profile

## License

This project is licensed under the terms of the MIT license.
