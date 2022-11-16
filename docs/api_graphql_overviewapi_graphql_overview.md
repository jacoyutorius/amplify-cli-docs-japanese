https://docs.amplify.aws/cli/graphql/overview/

# 概要
Amplify CLI の GraphQL API カテゴリでは、データベースによってバックアップされた新しい GraphQL API を簡単に作成することができます。GraphQL スキーマを定義するだけで、Amplify CLI がスキーマを AWS AppSync や Amazon DynamoDB などで動作する完全な GraphQL API に自動的に変換します。

## 最初のテーブルを作成する
まず、以下を実行して GraphQL API をセットアップします。
```bash
amplify add api
```

```console
? Select from one of the below mentioned services:
> GraphQL
? Here is the GraphQL API that we will create. Select a setting to edit or continue
> Continue
? Choose a schema template:
> Single object with fields (e.g., “Todo” with ID, name, description)
...
Edit your schema at <...>/schema.graphql or place .graphql files in a directory at <...>/schema
✔ Do you want to edit the schema now? (Y/n)
> yes
Edit the file in your editor: <...>/schema.graphql
✅ Successfully added resource new locally
```

デフォルト値を受け入れると、コード エディターに Todo アプリの GraphQL スキーマが表示されます。

```graphql
# This "input" configures a global authorization rule to enable public access to
# all models in this schema. Learn more about authorization rules here: https://docs.amplify.aws/cli/graphql/auth
input AMPLIFY { globalAuthRule: AuthRule = { allow: public } } # FOR TESTING ONLY!

type Todo @model {
  id: ID!
  name: String!
  description: String
}
```
GraphQL の `type` に `@model` ディレクティブを指定すると、自動的に新しい DynamoDB データベーステーブルがバックされます。

> **Warning**
>
> `input AMPLIFY { globalAuthRule: AuthRule = { allow: public }. }`を使用すると、認証ルールを気にすることなく、すぐに始めることができます。[認可ルール](https://docs.amplify.aws/cli/graphql/authorization-rules/)のセクションを確認し、GraphQL APIに適切なアクセス制御を設定してください。

それでは、変更した内容をクラウドにデプロイしてみましょう。
```bash
amplify push
```
これで完了です。これでAPIとデータベーステーブルのセットアップは完了です。

## アプリコードのセットアップする
Amplify ライブラリを使用して、アプリを GraphQL エンドポイントに接続します。

`yarn` または `npm` を使用して、アプリに Amplify ライブラリを追加します。
```bash
npm install aws-amplify
```

アプリのエントリポイント（App.js）で、設定ファイルをインポートして読み込みます。

```js
import { Amplify, API, graphqlOperation } from 'aws-amplify';
import awsconfig from './aws-exports';
Amplify.configure(awsconfig);
```

## 最初のレコードを追加する
次に、GraphQL APIからクエリを発行してみましょう。以下の手順で、Reactアプリからクエリを発行してみましょう。
```js
import { API } from 'aws-amplify'
import { createTodo, updateTodo, deleteTodo } from './graphql/mutations'
import { listTodos } from './graphql/queries'
```

次に、GraphQL APIを呼び出して、最初のTodoアイテムを作成します。
```js
const result = await API.graphql(graphqlOperation(createTodo, {
  input: {
    name: 'My first todo!'
  }
}))
```

## テーブルからレコードを取得する
GraphQL のクエリ文を使って、アプリ内のすべての ToDo をリストアップします。

```js
const result = await API.graphql(graphqlOperation(listTodos))
console.log(result)
```

上記で作成したレコードが表示されるはずです。`My first todo!` と表示されます。

## レコードを更新する
レコードを更新するには、GraphQL update mutationを使用します。

```js
const result = await API.graphql(graphqlOperation(updateTodo, {
  input: {
    id: "<...>",
    name: "My first updated todo!"
  }
}))
console.log(result)
```

resultには、更新された値である `My first updated todo!` が格納されているはずです。

## レコードを削除する
データベースをクリーンアップしましょう。delete mutation を使って、Todo を削除します。

```js
const result = await API.graphql(graphqlOperation(deleteTodo, {
  input: {
    id: "<...>",
  }
}))
console.log(result)
```
結果の出力は、レコードが正常に削除されたことを示すはずです!

## スキーマの更新
API を更新したい場合は、プロジェクトの `amplify/backend/api/<api-name>/schema.graphql` ファイル (`amplify/backend/api/<api-name>/build` フォルダ内のものではない) を開き、お気に入りのコードエディタで編集してください。amplify/backend/api/<api-name>/schema.graphql` ファイルを実行してコンパイルすることができます。

```bash
amplify api gql-compile
```

を実行して、コンパイルされたスキーマの出力を `backend/api/~apiname~/build/schema.graphql` で確認します。

その後、更新された変更をプッシュすることができます。

```bash
amplify push
```

次のスキーマの更新では、基礎となる DynamoDB テーブルを置き換える必要があります。

1. モデルの削除または名前変更
1. モデルの[主キー](https://docs.amplify.aws/cli/graphql/data-modeling/#configure-a-primary-key)の変更
1. モデルのローカル セカンダリ インデックスの変更 ( [secondaryKeyAsGSI](https://docs.amplify.aws/cli/reference/feature-flags/#secondaryKeyAsGSI)がオフになっているプロジェクトにのみ適用されます)

これらの更新の 1 つ以上を使用してスキーマの変更をプッシュしようとすると、置換が必要なテーブルのすべてのデータが失われることを説明するエラー メッセージが表示されます。デプロイを続行することを確認するには、次を実行します。

```bash
amplify push --allow-destructive-graphql-schema-updates
```

> **Note**
>
> 通常、このコマンドは開発中にのみ使用してください。
> 
> 本番 API に重大な変更を加えているが、影響を受けるテーブルのデータを保持したい場合は、実行する前に[バックアップを作成できます](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/CreateBackupAWS.html)。
> `amplify push --allow-destructive-graphql-schema-updates`

## GraphQL API を再構築する
> **Note**
>
> Rebuild は本番環境では絶対に使用しないでください。

開発中、テスト データが悪い状態になったり、スキーマに一度に多くの変更を加えたい場合があります。このような場合、スキーマをサポートするすべてのテーブルを「再構築」することができます。これを行うには、次を実行します。

```bash
amplify rebuild api
```

これにより、スキーマ内のモデルをサポートするすべてのテーブルが再作成されます。ALL TABLES の ALL DATA が削除されます。

## 次のステップ
成功です! データベーステーブルをバックにしたGraphQL APIを作成する方法と、アプリからクエリーとミューテーションを実行する方法を学びました。

AmplifyのGraphQL API機能には、まだまだ多くの発見があります。詳しくはこちら。
- [データベース テーブルとそのア​​クセス パターンをモデル化する方法](https://docs.amplify.aws/cli/graphql/data-modeling/)
- [きめ細かい承認ルールで API を保護する](https://docs.amplify.aws/cli/graphql/authorization-rules/)
- [異なるデータベース モデル間の関係を作成する](https://docs.amplify.aws/cli/graphql/data-modeling/#setup-relationships-between-models)
- [カスタム ビジネス ロジックを GraphQL API に追加する](https://docs.amplify.aws/cli/graphql/custom-business-logic/)
- [検索と結果の集計クエリを実行する](https://docs.amplify.aws/cli/graphql/search-and-result-aggregations/)
- [機械学習サービスに接続する](https://docs.amplify.aws/cli/graphql/connect-to-machine-learning-services/)
- [事例と解決策](https://docs.amplify.aws/cli/graphql/examples-and-solutions/)