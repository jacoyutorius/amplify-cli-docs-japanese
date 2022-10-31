https://docs.amplify.aws/cli/

# Amplify CLI

Amplify Command Line Interface (CLI) は、アプリケーション用の AWSサービスを作成、統合、および管理するための統合ツールチェーンです。

![](https://docs.amplify.aws/assets/cli-b-roll.gif)

## 主な機能

### GraphQLによるデータモデリング

ほとんどのアプリケーションの中核にあるのはデータです。アプリケーション内のデータを簡単にモデリング化してアクセスできるため、バックエンドの構築や再構築に煩わされることなくコア機能やビジネス価値の提供に集中することができます。

GraphQL変換ライブラリを利用することで GraphQLスキーマディレクティブを使用してNoSQLデータベース、認証、OpenSearchエンジン、Lambda関数リゾルバ、関連、承認などの機能を備えた AWS AppSync GraphQL APIをデプロイできます。[詳しく知る](https://docs.amplify.aws/cli/graphql/overview/)

### 複数の環境

Amplify CLIは複数の環境をサポートしています（開発・QA・本番など）。CLIでプロジェクトを初期化すると、Amplifyバックエンドが作成されます。Amplifyのバックエンドは、あなたのプロジェクトに追加されたカテゴリのコンテナです。すべてのバックエンド環境と追加されたカテゴリは、Amplifyコンソールで確認することができます。[詳しく知る](https://docs.amplify.aws/cli/teams/overview/)

### 拡張性

AWS Amplifyを利用することで、フルスタックなWeb/モバイルアプリケーションをリリースできます。AWS Amplify の拡張機能により、開発者は AWS バックエンドとデプロイ機能を柔軟にカスタマイズできます。
Amplifyで生成されたバックエンドリソースを再構成して特定のユースケースに合わせて最適化したり、Amplifyのデプロイ操作を変更して、ニーズの進化に合わせて企業のDevOpsガイドラインに準拠することができます。


### ローカル環境でのモック

Amplifyは、API（AWS AppSync）、ストレージ（Amazon DynamoDBやAmazon S3）、ファンクション（AWS Lambda）、ホスティング等の機能をクラウド環境にデプロイする前にローカルサーバーでモックしたりテストすることができます。
Amplifyプロジェクトを初期化後、以下のコマンドを実行することでモックサーバーが起動します。[詳しく知る](https://docs.amplify.aws/cli/usage/mock/)

```bash
amplify mock
```

### サーバーレスコンテナ

Amplifyは、アプリケーションを構築するための AWS Lambda および AWS Fargate コンピューティング オプションをサポートし、インフラストラクチャ内での完全な制御と統合を提供します。Lambda関数は、S3 や DynamoDB などのイベントソースからのトリガーに加えて、GraphQL および REST API で使用できます。
同様に、DockerfileまたはDocker Composeファイルを使用して、サーバーレスコンテナを自動的に構築し、Amazon Elastic Container Service にデプロイできます。[詳しく知る](https://docs.amplify.aws/cli/usage/containers/)
