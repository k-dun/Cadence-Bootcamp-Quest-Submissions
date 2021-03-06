1. Role of scripts is to read the data, not modify it.

2. Transaction has to be mutually agreed on. Once you approve the other end of the transaction it means you consent for the transaction to have access to the data in your account and that's the purpose of object AuthAccount.

3. "Prepare" phase's purpose is to access the data in your account. "Execute" can't do that and instead is responsible for calling functions and modifying data on the blockchain.

4.

Smart contract:

```cadence
pub contract HelloWorld {

    pub var greeting: String
    pub var myNumber: Int

    pub fun changeGreeting(newGreeting: String) {
        self.greeting = newGreeting
    }

    pub fun updateMyNumber(newNumber: Int) {
        self.myNumber = newNumber
    }

    init() {
        self.greeting = "Hello, World!"
        self.myNumber = 0
    }

}
```

Transaction:

```cadence
import HelloWorld from 0x01

transaction(myNewNumber: Int) {

  prepare(signer: AuthAccount) {}

  execute {
    HelloWorld.updateMyNumber(newNumber: myNewNumber)
  }
}
```

Script:

```cadence
import HelloWorld from 0x01

pub fun main(): Int {

  return HelloWorld.myNumber

}
```
