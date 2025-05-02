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
  ```

* **PKL CLI**
  Documentation: [https://pkl-lang.org/main/current/pkl-cli/index.html](https://pkl-lang.org/main/current/pkl-cli/index.html)

## Type Definition File (`types.pkl`)

The `types.pkl` file includes definitions such as `SwiftOpenAPIGeneratorConfig`, `DocumentFilter`, and others.

* To leverage IDE (IntelliJ / VS Code) autocomplete and type checking, copy `types.pkl` into your project and import it locally.
* Feel free to copy or modify the contents of the file as needed.

## Defining Your Own Configuration File

Create your own `openapi-generator-config.pkl`, then run the PKL command to emit YAML.

Below is an example assuming you have copied `types.pkl` to `Sources/App/types.pkl`. You would then create `Sources/App/openapi-generator-config.pkl` like this:

```pkl
import "./types.pkl" as OpenAPIGenerator

config: OpenAPIGenerator.Config = new {
  generate = new Listing {
    "types"
    "server"
  }
}
output {
  value = config
  renderer = new YamlRenderer {}
}
```

Add any of the supported top-level keys—such as `additionalImports`, `filter`, or `namingStrategy`—inside the `config` block as required.

## Generating `openapi-generator-config.yaml`

Run:

```bash
pkl eval ./Sources/App/openapi-generator-config.pkl \
  > ./Sources/App/openapi-generator-config.yaml
```

