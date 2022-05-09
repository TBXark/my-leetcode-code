# 50. Pow(x, n)

### 2017-02-28

Implement pow(*x*, *n*).



# Solution

```swift
class Solution {
    func myPow(_ x: Double, _ n: Int) -> Double {
        if n == 0 {
            return 1
        } else if n > 0 {
            let a = n / 2
            let b = n % 2
            let p = a == 1 ? x : myPow(x, a)
            let q = b == 1 ? x : myPow(x, b)
            return q * p * p
        }  else {
            return myPow(1/x, -n)
        }

    }
}
```

