# Degen Token (ERC-20): Unlocking the Future of Gaming
The DegenToken contract is an ERC20-compliant token implemented on the Ethereum blockchain. It enables the creation, transfer, and management of tokens within a decentralized gaming ecosystem.

## Description
The provided facilitates token-based interactions within the gaming environment, supporting rewards, transactions, and in-game purchases.

Key features include:

1. **Token minting:** Owners can create new tokens and distribute them to specific addresses.
2. **Token transfer:** Holders can transfer tokens to other addresses.
3. **In-game shop:** Players can redeem tokens for items listed in the shop, each with a corresponding price.
4. **Token burning:** Holders can destroy (burn) tokens, removing them from circulation.
5. **Ownership management:** The contract owner can update item prices, renounce ownership, and retain administrative control over the contract.

Overall, the contract facilitates token-based interactions within the gaming environment, supporting rewards, transactions, and in-game purchases.

### Executing Program
To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., myToken.sol). Copy and paste the following code into the file:


```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/utils/math/SafeMath.sol";

contract DegenToken is ERC20, Ownable {
    using SafeMath for uint256;

    mapping(uint256 => uint256) public itemPrices;

    constructor() ERC20("Degen", "DGN") Ownable(msg.sender) {
        itemPrices[1] = 100;
        itemPrices[2] = 200;
        itemPrices[3] = 50;
        itemPrices[4] = 10;
    }

    function mintTokens(address _to, uint256 _amount) public onlyOwner {
        _mint(_to, _amount);
    }

    function transferTokens(address _to, uint256 _amount) public {
        require(balanceOf(msg.sender) >= _amount, "Transfer Failed: Insufficient balance.");
        _transfer(msg.sender, _to, _amount);
    }

    function listShopItems() external pure returns (string memory) {
        return "The items on sale: {1} Rare Degen Sword (100) {2} Legendary Degen Armor (200) {3} Epic Degen Potion (50) {4} Common Degen Scroll (10)";
    }

    function redeemTokens(uint256 _item) public {
        require(itemPrices[_item] > 0 && _item <= 4, "Item is not available.");
        require(balanceOf(msg.sender) >= itemPrices[_item], "Redeem Failed: Insufficient balance.");
        transfer(owner(), itemPrices[_item]);
    }
    
    function burnTokens(uint256 _amount) public {
        require(balanceOf(msg.sender) >= _amount, "Burn Failed: Insufficient balance.");
        _burn(msg.sender, _amount);
    }

    function getBalance() external view returns (uint256) {
        return balanceOf(msg.sender);
    }

    function updateItemPrice(uint256 _item, uint256 _price) public onlyOwner {
        require(_item <= 4, "Item is not available.");
        itemPrices[_item] = _price;
    }

    function renounceOwnership() public virtual onlyOwner override{
        emit OwnershipTransferred(owner(), address(0));
        super.renounceOwnership();
    }
}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile myToken.sol" button.

To deploy the contract, click on the "Deploy and Run Transactions" button. This will open a new window that allows you to deploy the contract. Do not forget to select the “MyToken” contract before deploying.

#### Authors
NTCIAN Ann Loraine S. Ching | Discord @annching

##### License
This project is licensed under the MIT License - see the LICENSE.md file for details.
