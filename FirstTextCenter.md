## VerticalAlignment: FirstTextCenter

``` swift
extension VerticalAlignment {
    private struct FirstTextCenter: AlignmentID {
        static func defaultValue(in context: ViewDimensions) -> CGFloat {
            let firstTextHeight = context[.firstTextBaseline] + (context.height - context[.lastTextBaseline])
            return firstTextHeight / 2
        }
    }

    fileprivate static let firstTextCenter = VerticalAlignment(FirstTextCenter.self)
}
```
