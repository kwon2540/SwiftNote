## FormatStyle+Extension

``` swift
// FormatStyle : @available(macOS 12.0, iOS 15.0, tvOS 15.0, watchOS 8.0, *)
struct TimerIntegerStyle: FormatStyle {

    func format(_ value: Int) -> String {
        let formatter = DateComponentsFormatter()
        formatter.unitsStyle = .positional
        formatter.allowedUnits = [.minute, .second]
        return formatter.string(from: TimeInterval(value)) ?? "-:--"
    }
}

extension FormatStyle where Self == TimerIntegerStyle {

    static var timer: TimerIntegerStyle { .init() }
}

// Usage
let second: Int = 300
second.formatted(.timer) // "5:00"
```
