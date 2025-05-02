# Swift OpenAPI Generator PKL 型定義

<a href="LICENSE">
  <img src="https://design.vapor.codes/images/mitlicense.svg" alt="MIT License">
</a>

このリポジトリは、Apple の [swift-openapi-generator](https://github.com/apple/swift-openapi-generator) で使う設定ファイル（
`openapi-generator-config.yaml`）を、PKL を使って型安全に生成するための型定義PKLです

## 必要条件

* macOS + Homebrew

  ```bash
  brew install pkl
  ```
* PKL CLI
  ドキュメント: [https://pkl-lang.org/main/current/pkl-cli/index.html](https://pkl-lang.org/main/current/pkl-cli/index.html)

## 型定義ファイル (`types.pkl`)

`types.pkl` には、`SwiftOpenAPIGeneratorConfig` や `DocumentFilter` などの型定義が含まれます。

* **IDE（IntelliJ / VS Code）の補完や型チェックを利用** したい場合は、ローカルに`types.pkl`をコピーして使うことをおすすめします。
* ファイルの内容は自由にコピー・改変して構いません。

## 独自設定ファイルの定義方法

ユーザー自身で `openapi-generator-config.pkl` を定義し、その上で PKL コマンドを実行して YAML を生成します。

以下は`Sources/App/types.pkl`に`types.pkl`をコピーして配置した場合に`Sources/App/openapi-generator-config.pkl`
を作成する前提としたサンプルです。

```pkl
amends "./types.pkl"

generate {
  "client"
  "server"
}
namingStrategy = "idiomatic"
```

必要に応じて、`config` ブロック内に `additionalImports` や `filter`、`namingStrategy` などを追加してください。

## `openapi-generator-config.yaml` の生成方法

```shell
pkl eval ./Sources/App/openapi-generator-config.pkl > ./Sources/App/openapi-generator-config.yaml
```

