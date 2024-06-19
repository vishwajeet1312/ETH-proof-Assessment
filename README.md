 MyToken Smart Contract
This document provides an overview and usage guide for the `MyToken` smart contract. This Solidity contract implements a basic ERC20 like token, allowing for minting and burning of tokens.
 Features
 Token Name: Khichi Token Abbreviation: VSK Total Token Supply: Variable, based on minting and burning actions.
 Function used in it 
mint
Creates new tokens and assigns them to a specified address.
Parameters in it :`Addr` address to receive the newly minted tokens.`Val`: The amount of tokens to mint.
Increases the `Token_TotalSupply` by the specified `Val` and adds the `Val` to the balance of `Addr`.
burn
Description: Removes tokens from a specified address's balance.
Parameters in it : `Addr`: The address from which tokens will be burned. `Val`: The amount of tokens to burn.
Decreases the `Token_TotalSupply` by the specified `Val` and deducts the `Val` from the balance of `Addr`, provided the address has sufficient tokens.
function mint(address Addr, uint Val) public
This increases the total token supply by 100 and adds 100 tokens to `0xYourAddress`.
burning Tokens To burn tokens, call the `burn` function with the address and the number of tokens to be burned. Ensure the address has enough tokens before calling this function.
function burn(address Addr, uint Val) public
How to  Execute the Program
To run this smart contract, you can use Remix, an online Solidity IDE. Follow these steps:
a)	Go to Remix: Visit [Remix](https://remix.ethereum.org/).
b)	Create a New File: Click on the "+" icon in the lefthand sidebar and save the file with a `.sol` extension (e.g., `MyToken.sol`).
c)	Copy and Paste the Code: Copy the following code and paste it into the new file.

// SPDXLicenseIdentifier: MIT
pragma solidity ^0.8.18;

contract MyToken {
    string public Token_Name = "Khichi";
    string public Token_Abbrv = "vsk";
    uint public Token_TotalSupply = 0;

    mapping(address => uint) public Balance;

    function mint(address Addr, uint Val) public {
        Token_TotalSupply += Val;
        Balance[Addr] += Val;
    }
    function burn(address Addr, uint Val) public {
        if (Balance[Addr] >= Val) {
            Token_TotalSupply = Val;
            Balance[Addr] = Val;
        }
    }
}

Click on the "Solidity Compiler" tab in the lefthand sidebar. Select the compiler version `0.8.18` (or another compatible version) and click the "Compile MyToken.sol" button.
Navigate to the "Deploy & Run Transactions" tab in the lefthand sidebar. Select the `MyToken` contract from the dropdown menu and click the "Deploy" button.
Once deployed, we can interact with the contract by calling the `mint` and `burn` functions. Select the deployed contract in the lefthand sidebar, and call the desired function with the appropriate parameters.
