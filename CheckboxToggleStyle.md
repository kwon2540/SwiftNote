## SwiftUI: CheckboxToggleStyle

``` swift
extension ToggleStyle where Self == CheckboxToggleStyle {

    public static func checkbox(labelsHidden: Bool = true) -> CheckboxToggleStyle {
        return CheckboxToggleStyle(labelsHidden: labelsHidden)
    }
}

public struct CheckboxToggleStyle: ToggleStyle {
    public var isLabelsHidden: Bool

    public init(labelsHidden: Bool = true) {
        self.isLabelsHidden = labelsHidden
    }

    public func makeBody(configuration: Configuration) -> some View {
        Button {
            configuration.isOn.toggle()
        } label: {
            HStack(spacing: 8) {
                Image(.icCheckbox)
                    .resizable()
                    .opacity(configuration.isOn ? 1 : 0)
                    .background(
                        roundedRectangle
                            .fill(configuration.isOn ? .red : .clear)
                    )
                    .overlay(
                        roundedRectangle
                            .strokeBorder(configuration.isOn ? Color.clear : Color.black)
                    )
                    .frame(width: 20, height: 20)
                    .padding(6)

                if !isLabelsHidden {
                    configuration.label
                        .foregroundColor(.black)
                        .multilineTextAlignment(.leading)
                }
            }
        }
    }

    private var roundedRectangle: RoundedRectangle {
        RoundedRectangle(cornerRadius: 3)
    }
}
```
