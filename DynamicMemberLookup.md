## DynamicMemberLookup

```swift
enum MyEnum {
    case a(value: Value = Value())
    case b(value: Value = Value())

    struct Value {
        var value = "value"
    }
}

private let myEnum: MyEnum = .a()

if case let .a(value) = myEnum {
    print(value.value) // value
}

//---------------------------------------------------------------

@dynamicMemberLookup
enum MyEnum2 {
    case a(value: Value = Value())
    case b(value: Value = Value())

    subscript<T>(dynamicMember keyPath: KeyPath<Value, T>) -> T {
        switch self {
        case .a(let value):
            return value[keyPath: keyPath]
        case .b(let value):
            return value[keyPath: keyPath]
        }
    }

    struct Value {
        var value = "value"
    }
}

private let myEnum2: MyEnum2 = .a()

print(myEnum2.value) // value
```
