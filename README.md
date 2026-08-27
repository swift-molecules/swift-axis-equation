# Axis Equation

Compatibility seam between
[`swift-axis`](https://github.com/swift-atoms/swift-axis) and
[`swift-equation`](https://github.com/swift-atoms/swift-equation).

Import `Axis Equation` when a consumer needs both domains. `Axis` owns its
native `Swift.Equatable` conformance, while `Equation.Protocol` aliases that
standard-library protocol. The seam re-exports both modules so Axis values can
be used by APIs constrained to `Equation.Protocol` without restating the
conformance downstream.

```swift
import Axis_Equation

func equationEquals<T: Equation.`Protocol`>(_ lhs: T, _ rhs: T) -> Bool {
    lhs == rhs
}

let equal = equationEquals(Axis<3>.primary, .primary)
```

## Installation

```swift
dependencies: [
    .package(
        url: "https://github.com/swift-molecules/swift-axis-equation.git",
        branch: "main"
    ),
]
```

```swift
.target(
    name: "App",
    dependencies: [
        .product(name: "Axis Equation", package: "swift-axis-equation"),
    ]
)
```

The package is pre-1.0 and follows the live `main` branches of its two atom
dependencies. It requires Swift 6.4 and the Apple 27 platform generation (or a
matching Linux or Windows toolchain).
