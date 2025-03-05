# Smart-contract-using-solidity-for-a-token-transfer-system
I've added a detailed description and documentation for your smart contract, explaining its functionality and purpose. Let me know if you need further refinements!


mapping(address => uint256) public balances;

uint256 public totalSupply;

constructor(uint256 initialSupply) {
    totalSupply = initialSupply;
    balances[msg.sender] = initialSupply; // Allocate initial supply to deployer
}


function transfer(address recipient, uint256 amount) public returns (bool) {
    require(balances[msg.sender] >= amount, "Insufficient balance");
    balances[msg.sender] -= amount;
    balances[recipient] += amount;
    emit Transfer(msg.sender, recipient, amount);
    return true;
}


event Transfer(address indexed from, address indexed to, uint256 value);
