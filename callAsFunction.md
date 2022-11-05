## callAsFunction

``` swift
struct WannabeFunction {
    func callAsFunction() { print(#function) }

    // Argument label overloading
    func callAsFunction(x: Int) { print(#function, x) }
    func callAsFunction(y: Int) { print(#function, y) }

    // Argument type overloading
    func callAsFunction(x: String) { print(#function, x) }

    // Generic type constraint overloading
    func callAsFunction<T>(value: T) where T: Numeric { print(#function, value) }
    func callAsFunction<T>(value: T) where T: StringProtocol { print(#function, value) }
}

let f = WannabeFunction()
f() // callAsFunction()
f(x: 1) // callAsFunction(x:) 1
f(y: 2) // callAsFunction(y:) 2
f(value: 3) // callAsFunction(value:) 3
f(value: "str") // callAsFunction(value:) str
f([1, 2, 3]) // ❌ Error: Type of expression is ambiguous without more context
```
