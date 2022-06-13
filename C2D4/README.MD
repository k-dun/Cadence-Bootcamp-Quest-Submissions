Smart contract: 
```cadence
pub contract MedicalRecords {

    pub var profiles: {Address: MedicalProfile}
    
    pub struct MedicalProfile {
        pub let firstName: String
        pub let lastName: String
        pub let bloodType: String
        pub let age: Int
        pub let diabetes: Bool
        pub let account: Address

        init(_firstName: String, _lastName: String, _bloodType: String, _age: Int, _diabetes: Bool, _account: Address) {
            self.firstName = _firstName
            self.lastName = _lastName
            self.bloodType = _bloodType
            self.age = _age
            self.diabetes = _diabetes
            self.account = _account
        }
    }

    pub fun addMedicalProfile(firstName: String, lastName: String, bloodType: String, age: Int, diabetes: Bool, account: Address) {
        let newProfile = MedicalProfile(_firstName: firstName, _lastName: lastName, _bloodType: bloodType, _age: age, _diabetes: diabetes, _account: account)
        self.profiles[account] = newProfile
    }

    init() {
        self.profiles = {}
    }

}
```

Transaction: 
```cadence
import MedicalRecords from 0x01

transaction(firstName: String, lastName: String, bloodType: String, age: Int, diabetes: Bool, account: Address) {

    prepare(signer: AuthAccount) {}

    execute {
        MedicalRecords.addMedicalProfile(firstName: firstName, lastName: lastName, bloodType: bloodType, age: age, diabetes: diabetes, account: account)
        log("We're done.")
    }
}
```

Script: 
```cadence
import MedicalRecords from 0x01

pub fun main(account: Address): MedicalRecords.MedicalProfile {
    return MedicalRecords.profiles[account]!
}
```
