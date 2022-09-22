## SwiftUI: DimmedBackground

``` swift
struct DimmedBackground: UIViewRepresentable {

    func makeUIView(context: Context) -> UIView {
        let view = UIView()
        DispatchQueue.main.async {
            view.superview?.superview?.backgroundColor = UIColor.app(.overlay)
        }
        return view
    }

    func updateUIView(_ uiView: UIView, context: Context) {
    }
}
```
