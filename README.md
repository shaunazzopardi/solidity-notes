# solidity-notes
Notes on Solidity I intend to keep while learning and getting used to the Solidity language for smart contracts on Ethereum.


Arrays as arguments
-----

Arrays cannot always be passed as argument of public functions, but they can always be passed as arguments of internal or private functions. Only address arrays can be passed as arguments from outside the contract, while other kinds, such as string arrays, cannot but have to be deserialised by the smart contract itself. For example if we want to pass the string array ["hh","yy"], we have to pass as a string with some kind of delimiter or separator, e.g. "hh|yy", we can then identify from within the smart contract.


Delegatecalls
-----

Contracts can call other contracts. One way of doing this is through delegate calls, which allow the called contract to operate within the caller contract. Take care that the called contract has the same storage variables as the caller contract (and possibly more, i.e. the storage of the called contract is a superset of the storage of the caller contract, or the caller storage is a subset of the called storage), otherwise the delegate call will have no effect.

Also, delegate calls will always return true if there is no throwing in the called method (e.g. through the now deprecated <i>throw</i>, through <i>revert</i>, or through a failed <i>requires</i>).

View
----

Functions declared with the <i>view</i> tag cannot affect state.

Pure
----

Functions declared with the <i>pure</i> tag cannot affect state, or read from it and can only depend on the function arguments, excluding msg (except the signature msg.sig and msg.data), block, and tx. They can also only call pure functions. So pure functions are stateless functions.

Storage and Memory
----

<i>BettingContract memory name = BettingContract(_index);</i> is a <b>pointer</b> to the contract at <i>_index</i>, and thus can actually change the contract at that index. 

<i>BettingContract stoarage name = BettingContract(_index);</i> creates a <b>copy</b> of the contract at <i>_index</i>, and thus can actually change the contract at that index. 


[1] http://solidity.readthedocs.io/en/develop/index.html
