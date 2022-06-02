![This is an image](https://github.com/k-dun/quest-submissions/blob/main/images/Screenshot%202022-06-02%20at%2019.55.44.png)

Smart contract:

```cadence
pub contract JacobTucker {

  pub let is: String

  init() {
    self.is = "the best"
  }
}
```

Script:

```cadence
import JacobTucker from 0x03

pub fun main(): String {
  return JacobTucker.is
}
```
