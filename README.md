# Swift OpenAPI Generator PKL Type Definitions

<a href="LICENSE">
  <img src="https://design.vapor.codes/images/mitlicense.svg" alt="MIT License">
</a>

[日本語](./README.ja.md)

This repository provides PKL-based type definitions for generating the `openapi-generator-config.yaml` file used by Apple’s [swift-openapi-generator](https://github.com/apple/swift-openapi-generator), ensuring type-safe configuration.

## Requirements

- **macOS + Homebrew**

  ```bash
  brew install pkl
````

* **PKL CLI**
  Documentation: [https://pkl-lang.org/main/current/pkl-cli/index.html](https://pkl-lang.org/main/current/pkl-cli/index.html)

## Type Definition File (`types.pkl`)

The `types.pkl` file includes definitions such as `SwiftOpenAPIGeneratorConfig`, `DocumentFilter`, and others.

* To leverage IDE (IntelliJ / VS Code) autocomplete and type checking, copy `types.pkl` into your project.
* Feel free to copy or modify its contents as needed.

## Defining Your Own Configuration

Create an `openapi-generator-config.pkl` that amends `types.pkl` and adds or overrides fields. For example:

```pkl
amends "./types.pkl"

generate {
  "client"
  "server"
}
namingStrategy = "idiomatic"
```

Add other supported keys—such as `additionalImports` or `filter`—as needed.

## Generating `openapi-generator-config.yaml`

```bash
pkl eval ./Sources/App/openapi-generator-config.pkl \
  > ./Sources/App/openapi-generator-config.yaml
```