ETH Proof Beginner Course

First, we have created public variables that store the details about the coins: Token Name, Token Abbrv., and Total Supply as Token_Name, Token_Abbrv, and Token_TotalSupply, respectively.

Second, we have created a public mapping of addresses to balances (address => uint) called Balance.

Then, we have created a mint function that takes two parameters: an address and a value. The function increases the total supply by that value and increases the balance of the specified address by the same amount.

function mint(address Addr, uint Val) public {
    Token_TotalSupply += Val;
    Balance[Addr] += Val;
}

Finally, we have created a burn function, which works the opposite of the mint function, as it destroys tokens. It takes an address and a value just like the mint function. It then deducts the value from the total supply and from the balance of the specified address. The function also has conditionals to ensure the balance of the address is greater than or equal to the amount that is supposed to be burned.

function burn(address Addr, uint Val) public {
    if (Balance[Addr] >= Val) {
        Token_TotalSupply -= Val;
        Balance[Addr] -= Val;
    }
}



