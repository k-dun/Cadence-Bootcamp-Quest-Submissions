1.

```cadence
pub fun main() {
  let favPeople = ["Baby","Girl","Demi"]
  log(favPeople)
}
```

2.

```cadence
pub fun main() {
  var socials: { String: UInt64} = {"Facebook": 1 , "Instagram": 4 , "Twitter": 5 , "Youtube": 3 , "Reddit": 0 , "LinkedIn": 2 }
}
```

3. Force-unwrapping returns the value of an optional, if it has value, or panics and aborts if it hasn't (nil).

```cadence
let a: Int? = nil
let b: Int? = 5

let c: Int = a! // since the value is nil the execution stops.
let d: Int = b! // returns 5
```
4. The error message means that the output type doesn't match the declared type that was expected. We are getting this error, because when accessing a value in a dictionary the returned value is always an optional type. To fix the error we need to use the force-unwrap operator, as shown below:

```cadence
pub fun main(): String {
  let thing: {Address: String} = { 0x01: "One", 0x02: "Two", 0x03: "Three" }
  return thing[0x03]!
}
```
