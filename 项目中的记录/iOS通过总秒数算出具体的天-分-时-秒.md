# iOS通过总秒数算出具体的天-分-时-秒

``` swift

var totalSec: Int = 10000000

let day = totalSec/24/60/60

let hour = totalSec/60/60%24

let min = totalSec/60%60

let sec = totalSec%60

```