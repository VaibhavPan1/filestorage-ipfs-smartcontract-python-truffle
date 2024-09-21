1. Run IPFS daemon, local ganache, mysql server
2. uncomment network config in truffle config file 
3. config file for mysql in config directory


4. create a table files in database of choice using following command: 
CREATE TABLE files (
    id INT AUTO_INCREMENT PRIMARY KEY,
    file_name VARCHAR(255) NOT NULL,
    cid VARCHAR(255) NOT NULL
);

5. init ipfs node (use version 0.7 and repo version 10)
6. solidity compiler (solc-js) version must match contract version
7. Solidity compiler versions 0.5.x and above no longer use the constant keyword in the ABI. Instead, the correct field is stateMutability: "view" or stateMutability: "pure" for functions that don’t modify or read the state.
8. Link truffle project to ganache 

#Steps to create and deploy smart contract using truffle: 
1. start truffle project using "truffle init"
2. write the smart contract in contracts folder
3. truffle compile
4. uncomment networks config in truffle-config.js file
5. write migration code in migrations, eg:
const MyContract = artifacts.require("MyContract");

module.exports = function(deployer) {
  deployer.deploy(MyContract, "Hello, World!"); // Constructor argument
};
6. deploy contract to ganache using truffle migrate --network development