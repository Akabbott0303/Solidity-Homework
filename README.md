# Sharing the Wealth with Smart Contracts

I'm on the team of a startup, at least in my imagination, and we want to build smart contracts to automate as much of the company's financial transactions as possible.  Our goals are to simplify our processes, make our financial transactions as transparent as possible, and to build an audit trail.  The tool that can help us meet our goals is blockchain technology.

A smart contract is a script that runs on a blockchain.  To write the (imaginary) company's (real) smart contracts, I used Solidity, a programming language that runs on many blockchains, mainly Ethereum compatible chains.  I used [Remix](https://remix.ethereum.org) to write and deploy my smart contract.
<details>
  
<summary>Associate Profit Splitter Contract</summary>
  
### About the Associate Profit Splitter Contract

This smart contract is used to divide Ethereum between three employees.  First, public variables, which can be seen by anyone on the Ethereum network, are created for each employee.  A constructor function creates the capability for the contract owner to assign a blockchain address to each employee as the contract is deployed.  The balance function returns the balance of the contract, and, in this case, should always return zero.  The contract is not designed to hold any value; rather, it is designed to transfer Ether to the three employees.  The balance function acts as a check to make sure that the contract is operating as expected.  The deposit function both allows for Ether to be deposited to the contract and transferred to each employee.  The function divides the deposited amount by three and sends a third to each employee.  Any remiander is sent back to the contract owner.  The last function is a fallback function that calls the deposit function.  This function ensures that any Ether sent to the contract is handled by the deposit function, which ensures that the Ether is transferred to each empolyee.  This way, no Ether can become locked into the contract, which does not have a withdraw function.

### Deploying and Using the Profit Splitter Contract

The contract was deployed by assigning the employee addresses using the constructor function, like so:

![Constructor_Function](/Screenshots/Constructor_Function.PNG)

Here is the address assignment:

![Employee_Addresses](/Screenshots/Employee_Addresses.PNG)

The contract's address on the Ropsten network is 0x5A4B07e741Ffd29Ba20A4112684FABF7e1d0c7ee.  With the contract deployed, I was able to send Ether to our three employees:

![Transaction_Ropsten](/Screenshots/Transaction_Ropsten.PNG)

![Transaction_Ropsten_Confirmation](/Screenshots/Transaction_Ropsten_Confirmation.PNG)

As expected, the contract balance is zero after the transaction was completed:

![Balance_Zero](/Screenshots/Balance_Zero.PNG)
  
The transaction shows up on the [Ropsten blockchain](https://explorer.anyblock.tools/ethereum/ethereum/ropsten):

![Block_Explorer](/Screenshots/Block_Explorer.PNG)

</details>

<details>
  
<summary>Tiered Profit Splitter Contract</summary>
  
### About the Tiered Profit Splitter Contract

The Tiered Profit Splitter smart contract is used to divide Ethereum between three employees using different percentages for each employee.  As in the Associate Profit Splitter contract, we first set the public variables and use a constructor function to assign employee addresses.  The balance function again should always return zero since this contract does not hold any funds.  The deposit function divides the deposited amount by specified percentages and sends each employee his or her designated percentage.  The remiander is sent to the highest paid employee.  This contract ends wtih a fallback function just like the other one did.

### Deploying and Using the Tiered Profit Splitter Contract

The contract was deployed by assigning the employee addresses as in the Associate Profit Splitter contract.

The contract's address on the Ropsten network is 0x3Cc16641BA844d7a34064e17bCE419574A6cD8Cc.  As with the first contract, I was able to send Ether to each employee:

![Transaction_Ropsten_2](/Screenshots/Transaction_Ropsten_2.PNG)

![Transaction_Ropsten_Confirmation_2](/Screenshots/Transaction_Ropsten_Confirmation_2.PNG)

As expected, like the first contract, the contract balance continually showed zero. 
  
The transaction for this contract shows up on the [Ropsten blockchain](https://explorer.anyblock.tools/ethereum/ethereum/ropsten):

![Block_Explorer_2](/Screenshots/Block_Explorer_2.PNG)

</details>
