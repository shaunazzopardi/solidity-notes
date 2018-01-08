# solidity-notes
Notes on Solidity I intend to keep while learning and getting used to the Solidity language for smart contracts on Ethereum.


Arrays as arguments
-----

Arrays cannot always be passed as argument of public functions, but they can always be passed as arguments of internal or private functions. Only address arrays can be passed as arguments from outside the contract, while other kinds, such as string arrays, cannot but have to be deserialised by the smart contract itself. For example if we want to pass the string array ["hh","yy"], we have to pass as a string with some kind of delimiter or separator, e.g. "hh|yy", we can then identify from within the smart contract.


Delegatecalls
-----

Contracts can call other contracts. One way of doing this is through delegate calls, which allow the called contract to operate within the caller contract. Take care that the called contract has the same storage variables as the caller contract (and possibly more, i.e. the storage of the called contract is a superset of the storage of the caller contract, or the caller storage is a subset of the called storage), otherwise the delegate call will have no effect.

Also, delegate calls will always return true if there is no throwing in the called method (e.g. through the now deprecated <i>throw</i>, through <i>revert</i>, or through a failed <i>requires</i>).
