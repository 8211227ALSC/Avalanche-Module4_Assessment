# ERC20Tokens
This project defines a smart contract named MyToken that implements the ERC20 standard token functionality. This contract creates a basic ERC20 token named "MyToken", where the owner can mint new tokens and users can burn their own tokens.

## Description
The provided Solidity code defines a smart contract called MyToken which serves as an implementation of the ERC20 standard token. It begins with directives specifying the compiler version and license. The contract imports the ERC20.sol file from the OpenZeppelin library to inherit the standard ERC20 functionality. Within the contract, there's a state variable owner, representing the address of the contract owner. The onlyOwner modifier is used to restrict certain functions to be accessible only by the contract owner. In the constructor, the contract initializes by setting the owner variable to the address that deployed the contract and mints an initial supply of tokens to that address. The mint function enables the contract owner to mint additional tokens and distribute them to specified addresses. Conversely, the burn function permits any user to burn a specified amount of their own tokens, thus reducing the total token supply. In summary, this contract provides a basic ERC20 token functionality where the owner can mint tokens and users can burn their own tokens as needed.

### Executing Program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., myToken.sol). Copy and paste the following code into the file:


```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract MyToken is ERC20 {
    address public tokenOwner;

    modifier onlyOwner() {
        require(msg.sender == tokenOwner, "Only owner can call this function");
        _;
    }

    constructor() ERC20("MyToken", "MTK") {
        tokenOwner = msg.sender;
        _mint(msg.sender, 1000000 * 10 ** decimals());
    }

    function mint(address to, uint256 amount) external onlyOwner {
        _mint(to, amount);
    }

    function burn(uint256 amount) external {
        _burn(msg.sender, amount);
    }

    function transfer(address to, uint256 amount) public override returns (bool) {
        _transfer(_msgSender(), to, amount);
        return true;
    }

    function transferFrom(address sender, address recipient, uint256 amount) public override returns (bool) {
        _transfer(sender, recipient, amount);
        _approve(sender, _msgSender(), allowance(sender, _msgSender()) - amount);
        return true;
    }
}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile myToken.sol" button.

To deploy the contract, click on the "Deploy and Run Transactions" button. This will open a new window that allows you to deploy the contract. Do not forget to select the “MyToken” contract before deploying.

In the deployment window “Deployed Contracts”, set the parameters for the balance, mint, and burn functions.

To mint new tokens, input the address of the recipient and the number of tokens you want to mint and click transact.

To burn tokens, input the address of the recipient and the number of tokens you want to burn and click transact.

To see current balances of the address, input the address of the recipient and the number of tokens you want to mint and click call. You can also see the total supply by clicking the “totalSupply” button.

#### Authors
NTCIAN Ann Loraine S. Ching | Discord @annching

##### License
This project is licensed under the MIT License - see the LICENSE.md file for details.
