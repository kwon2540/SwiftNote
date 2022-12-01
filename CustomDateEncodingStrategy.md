## Custom DateEncodingStrategy

``` swift
extension JSONEncoder.DateEncodingStrategy {
    static var birthDate: Self {
        let formatter = ISO8601DateFormatter()
        formatter.formatOptions = [.withFullDate, .withDashSeparatorInDate]
        return .custom { date, encoder in
            var container = encoder.singleValueContainer()
            let dateString = formatter.string(from: date)
            try container.encode(dateString)
        }
    }
}

// Usage
extension JSONEncoder {
    static let `default` = {
        let encoder = JSONEncoder()
        encoder.keyEncodingStrategy = .convertToSnakeCase
        encoder.dateEncodingStrategy = .birthDate // <- here
        return encoder
    }()
}
```
