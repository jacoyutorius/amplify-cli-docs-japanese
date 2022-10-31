

# IAMポリシー

https://docs.amplify.aws/cli/reference/iam/

Amplify CLIは全てのカテゴリでアクションを実行するための以下のIAMポリシーが必要です。必要に応じて　`Action` セクションに権限を追加したり削除することでカテゴリへの権限を付与または制限することができます。

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "amplify:CreateApp",
        "amplify:CreateBackendEnvironment",
        "amplify:CreateBranch",
        "amplify:DeleteApp",
        "amplify:DeleteBackendEnvironment",
        "amplify:DeleteBranch",
        "amplify:GetApp",
        "amplify:GetBackendEnvironment",
        "amplify:GetBranch",
        "amplify:ListApps",
        "amplify:ListBackendEnvironments",
        "amplify:ListBranches",
        "amplify:ListDomainAssociations",
        "amplify:UpdateApp",
        "apigateway:DELETE",
        "apigateway:GET",
        "apigateway:PATCH",
        "apigateway:POST",
        "apigateway:PUT",
        "appsync:CreateApiKey",
        "appsync:CreateDataSource",
        "appsync:CreateFunction",
        "appsync:CreateGraphqlApi",
        "appsync:CreateResolver",
        "appsync:CreateType",
        "appsync:DeleteApiKey",
        "appsync:DeleteDataSource",
        "appsync:DeleteFunction",
        "appsync:DeleteGraphqlApi",
        "appsync:DeleteResolver",
        "appsync:DeleteType",
        "appsync:GetDataSource",
        "appsync:GetFunction",
        "appsync:GetGraphqlApi",
        "appsync:GetIntrospectionSchema",
        "appsync:GetResolver",
        "appsync:GetSchemaCreationStatus",
        "appsync:GetType",
        "appsync:GraphQL",
        "appsync:ListApiKeys",
        "appsync:ListDataSources",
        "appsync:ListFunctions",
        "appsync:ListGraphqlApis",
        "appsync:ListResolvers",
        "appsync:ListResolversByFunction",
        "appsync:ListTagsForResource",
        "appsync:ListTypes",
        "appsync:StartSchemaCreation",
        "appsync:TagResource",
        "appsync:UpdateApiKey",
        "appsync:UpdateDataSource",
        "appsync:UpdateFunction",
        "appsync:UpdateGraphqlApi",
        "appsync:UpdateResolver",
        "appsync:UpdateType",
        "cloudformation:CreateChangeSet",
        "cloudformation:CreateStack",
        "cloudformation:CreateStackSet",
        "cloudformation:DeleteStack",
        "cloudformation:DeleteStackSet",
        "cloudformation:DescribeChangeSet",
        "cloudformation:DescribeStackEvents",
        "cloudformation:DescribeStackResource",
        "cloudformation:DescribeStackResources",
        "cloudformation:DescribeStacks",
        "cloudformation:DescribeStackSet",
        "cloudformation:DescribeStackSetOperation",
        "cloudformation:ExecuteChangeSet",
        "cloudformation:GetTemplate",
        "cloudformation:GetTemplateSummary",
        "cloudformation:ListStackResources",
        "cloudformation:UpdateStack",
        "cloudformation:UpdateStackSet",
        "cloudfront:CreateCloudFrontOriginAccessIdentity",
        "cloudfront:CreateDistribution",
        "cloudfront:DeleteCloudFrontOriginAccessIdentity",
        "cloudfront:DeleteDistribution",
        "cloudfront:GetCloudFrontOriginAccessIdentity",
        "cloudfront:GetCloudFrontOriginAccessIdentityConfig",
        "cloudfront:GetDistribution",
        "cloudfront:GetDistributionConfig",
        "cloudfront:TagResource",
        "cloudfront:UntagResource",
        "cloudfront:UpdateCloudFrontOriginAccessIdentity",
        "cloudfront:UpdateDistribution",
        "cognito-identity:CreateIdentityPool",
        "cognito-identity:DeleteIdentityPool",
        "cognito-identity:DescribeIdentity",
        "cognito-identity:DescribeIdentityPool",
        "cognito-identity:GetIdentityPoolRoles",
        "cognito-identity:ListIdentityPools",
        "cognito-identity:SetIdentityPoolRoles",
        "cognito-identity:TagResource",
        "cognito-identity:UpdateIdentityPool",
        "cognito-idp:AdminAddUserToGroup",
        "cognito-idp:AdminCreateUser",
        "cognito-idp:CreateGroup",
        "cognito-idp:CreateUserPool",
        "cognito-idp:CreateUserPoolClient",
        "cognito-idp:DeleteGroup",
        "cognito-idp:DeleteUser",
        "cognito-idp:DeleteUserPool",
        "cognito-idp:DeleteUserPoolClient",
        "cognito-idp:DescribeIdentityProvider",
        "cognito-idp:DescribeUserPool",
        "cognito-idp:DescribeUserPoolClient",
        "cognito-idp:GetUserPoolMfaConfig",
        "cognito-idp:ListIdentityProviders",
        "cognito-idp:ListTagsForResource",
        "cognito-idp:ListUserPoolClients",
        "cognito-idp:ListUserPools",
        "cognito-idp:UpdateGroup",
        "cognito-idp:UpdateUserPool",
        "cognito-idp:UpdateUserPoolClient",
        "dynamodb:CreateTable",
        "dynamodb:DeleteItem",
        "dynamodb:DeleteTable",
        "dynamodb:DescribeContinuousBackups",
        "dynamodb:DescribeTable",
        "dynamodb:DescribeTimeToLive",
        "dynamodb:ListStreams",
        "dynamodb:ListTables",
        "dynamodb:PutItem",
        "dynamodb:TagResource",
        "dynamodb:UpdateContinuousBackups",
        "dynamodb:UpdateItem",
        "dynamodb:UpdateTable",
        "dynamodb:UpdateTimeToLive",
        "es:AddTags",
        "es:CreateElasticsearchDomain",
        "es:DeleteElasticsearchDomain",
        "es:DescribeElasticsearchDomain",
        "events:DeleteRule",
        "events:DescribeRule",
        "events:ListRuleNamesByTarget",
        "events:PutRule",
        "events:PutTargets",
        "events:RemoveTargets",
        "geo:GetMapStyleDescriptor",
        "geo:GetMapGlyphs",
        "geo:GetMapSprites",
        "geo:GetMapTile",
        "geo:SearchPlaceIndexForPosition",
        "geo:SearchPlaceIndexForText",
        "geo:SearchPlaceIndexForSuggestions",
        "iam:AttachRolePolicy",
        "iam:CreatePolicy",
        "iam:CreatePolicyVersion",
        "iam:CreateRole",
        "iam:DeletePolicy",
        "iam:DeletePolicyVersion",
        "iam:DeleteRole",
        "iam:DeleteRolePermissionsBoundary",
        "iam:DeleteRolePolicy",
        "iam:DetachRolePolicy",
        "iam:GetPolicy",
        "iam:GetRole",
        "iam:GetRolePolicy",
        "iam:GetUser",
        "iam:ListAttachedRolePolicies",
        "iam:ListPolicyVersions",
        "iam:PassRole",
        "iam:PutRolePermissionsBoundary",
        "iam:PutRolePolicy",
        "iam:TagRole",
        "iam:UpdateRole",
        "kinesis:AddTagsToStream",
        "kinesis:CreateStream",
        "kinesis:DeleteStream",
        "kinesis:DescribeStream",
        "kinesis:DescribeStreamSummary",
        "kinesis:ListTagsForStream",
        "kinesis:PutRecords",
        "lambda:AddLayerVersionPermission",
        "lambda:AddPermission",
        "lambda:CreateEventSourceMapping",
        "lambda:CreateFunction",
        "lambda:DeleteEventSourceMapping",
        "lambda:DeleteFunction",
        "lambda:DeleteLayerVersion",
        "lambda:GetEventSourceMapping",
        "lambda:GetFunction",
        "lambda:GetFunctionConfiguration",
        "lambda:GetLayerVersion",
        "lambda:InvokeAsync",
        "lambda:InvokeFunction",
        "lambda:ListEventSourceMappings",
        "lambda:ListLayerVersions",
        "lambda:PublishLayerVersion",
        "lambda:RemoveLayerVersionPermission",
        "lambda:RemovePermission",
        "lambda:UpdateFunctionCode",
        "lambda:UpdateFunctionConfiguration",
        "lex:GetBot",
        "lex:GetBuiltinIntent",
        "lex:GetBuiltinIntents",
        "lex:GetBuiltinSlotTypes",
        "logs:DescribeLogStreams",
        "logs:GetLogEvents",
        "mobiletargeting:CreateApp",
        "mobiletargeting:DeleteApnsChannel",
        "mobiletargeting:DeleteApnsSandboxChannel",
        "mobiletargeting:DeleteApp",
        "mobiletargeting:DeleteEmailChannel",
        "mobiletargeting:DeleteGcmChannel",
        "mobiletargeting:DeleteSmsChannel",
        "mobiletargeting:GetApnsChannel",
        "mobiletargeting:GetApnsSandboxChannel",
        "mobiletargeting:GetApp",
        "mobiletargeting:GetEmailChannel",
        "mobiletargeting:GetGcmChannel",
        "mobiletargeting:GetSmsChannel",
        "mobiletargeting:UpdateApnsChannel",
        "mobiletargeting:UpdateApnsSandboxChannel",
        "mobiletargeting:UpdateEmailChannel",
        "mobiletargeting:UpdateGcmChannel",
        "mobiletargeting:UpdateSmsChannel",
        "rekognition:DescribeCollection",
        "s3:CreateBucket",
        "s3:DeleteBucket",
        "s3:DeleteBucketPolicy",
        "s3:DeleteBucketWebsite",
        "s3:DeleteObject",
        "s3:DeleteObjectVersion",
        "s3:GetBucketLocation",
        "s3:GetObject",
        "s3:ListAllMyBuckets",
        "s3:ListBucket",
        "s3:ListBucketVersions",
        "s3:PutBucketAcl",
        "s3:PutBucketCORS",
        "s3:PutBucketNotification",
        "s3:PutBucketPolicy",
        "s3:PutBucketWebsite",
        "s3:PutEncryptionConfiguration",
        "s3:PutObject",
        "s3:PutObjectAcl"
      ],
      "Resource": "*"
    }
  ]
}
```
 
# IAMロール と MFA

https://docs.amplify.aws/cli/reference/iam-roles-mfa/

オプションとして、共有された ~/.aws/config ファイルにロール用のプロファイルを定義することで、Amplify CLI が IAM ロールを引き受けるように設定することができます。
これは短期間の認証情報を含むAWS CLIの機能に似ています。
これは複数の開発者が1つまたは複数のAWSアカウントを所持し、チームワークフローにおいてカテゴリへの更新を制限したいときに便利です。

`amplify init` または `amplify configure project` コマンドの実行中にプロンプトが表示されたら、ロール用に設定されたプロファイルを選択することで、CLIは一時的な認証情報の取得・キャッシュ・リフレッシュの処理を制御します。
もし多要素認証(MFA)が有効な場合、Amplify CLIは一時的な認証情報を取得または更新する必要があるときにMFAトークンコードを入力するよう表示されます。

Amplify CLIは独自のキャッシュ機構を持っており、AWS CLIと同じキャッシュは使用しません。
一時的な認証情報は `~/.amplify/awscloudformation/cache.json` にキャッシュされます。このファイルを削除することで、キャッシュされた全ての認証情報を削除することができます。
特定のプロジェクトに関連するキャッシュされた一時的な認証情報のみを削除したい場合はそのプロジェクト内で `~/.amplify/awscloudformation/cache.json` またはそのエイリアスである `amplify aws reset-cache` を実行してください。

## IAMロールを作成して利用するためのガイド

以下は、IAMロールを作成し、Amplify CLIで利用できるようにする方法についての手順です。

セットアップには3つのパートがありますが、ここではこのような例を使って解説します。

Biz Corpが在庫管理Webポータルの開発をDev Corpに依頼することを決定し、Dev Corpが開発プロセスをスピードアップするためにAmplify CLIを使用すると仮定します。

### 1. ロールの設定(Biz Corp)

1. AWSマネージメントコンソールにログインし、[IAM](https://console.aws.amazon.com/iam/)の管理画面を開く。
2. ナビゲーションペインにて `ロール` を選択し、`ロールの作成`　を選択します。
3. 「信頼されたエンティティタイプ」で「AWSアカウント」を選択します。
4. 「アカウントID」にはDev CorpのAWSアカウントID（AWSリソースへのアクセスを許可したいアカウントID）

### 2. ユーザーを作成し、権限を付与する(Dev Corp)

### 3. ローカル開発環境を設定する(Dev Corp)


# ファイルとフォルダ

# Amplify　CLIでのデータ使用方法

# 診断

https://docs.amplify.aws/cli/reference/diagnose/

以下のコマンドを実行することで、気密性の低い設定をAmplifyのバックエンドと共有することができます。

```bash
amplify diagnose --send-report
```

CLIは気密性の低いファイルをzip形式で収集し、安全な場所に送信します。以下はCLIが収集・送信・保存するファイルです。

- [backend-config.json]: プロジェクトの提供する全てのカテゴリが含まれます。
- CloudFormation files: CLIの生成した、Amplifyリソースを生成するためのCloudFormationファイル。
- [cli.json](https://docs.amplify.aws/cli/reference/files/#clijson): feature flag構成。
- [amplify.state](https://docs.amplify.aws/cli/reference/files/#cli-inputsjson): functionカテゴリを呼び出すためのメタデータ。
- [parameters.json](https://docs.amplify.aws/cli/reference/files/#category-parametersjson) と cli-inputs.json。
- shema.sraphql または GraphQL APIのスキーマフォルダ。
- CloudFormationにカスタム拡張機能を提供する　override.ts
- パッケージファイルに格納されているfunctionカテゴリの依存情報。


zipファイルの送信に成功したすると、現在のプロジェクトの一意の識別子が表示されます。この識別子はサポートエンジニアがデバッグ目的でzipファイルにアクセスするのに必要となります。

```bash
Project Identifier: 56b5981ed6cf5caad90fb2f8aed150e2
```

### 自動レポート共有

Amplify　CLIを改善するために、CLI失敗に自動的にプロジェクト設定を共有することができます。
これはプロジェクトレベルの設定であり、プロジェクト毎に切り替えることができます。
以下のコマンドを実行することで無効化できます。

```bash
amplify diagnose --auto-send-off
```

有効化するには、

```bash
amplify diagnose --auto-send-on
```

CLIは `amplify diagnose --send-report`を実行することで以下のファイルを含む２つの追加ファイルを収集します。

- エラー詳細: エラー名、エラーメッセージ、スタックトレースを含みます。
- `amplify push` が実行されたときのCloudFormationの更新内容。

## セキュリティ

zipファイルの送信には公開暗号化・非公開暗号化方式で暗号化されます。残りのファイルは AES 256 ビット暗号化で保存されます。
ファイルは60日間保持され、その間にファイルは削除対象としてマークされます。ファイルはデバッグ目的でのみ使用され、チーム外で共有されることはありません。

# フィーチャーフラグ

https://docs.amplify.aws/cli/reference/feature-flags/

フィーチャーフラグを使用すると、Amplify CLIで特定の機能を微調整することができます。

これらは、機能の領域に基づいてセクションにグループ化されています。領域は、カテゴリまたはその他の範囲にすることができます。さまざまなタイプの機能フラグが定義されており、それらの有効期間はライフサイクルプロセスによって制御されます。

## フィーチャーフラグの種類

### Release

このタイプの機能フラグは、現在開発中のAmplify CLIの特定の機能を有効または無効にするために使用されます。これらの機能フラグは、機能がいちどリリースされると削除され、サポートされなくなります。

### Feature

Amplify CLIの歴史の中で、新しいプロジェクトに役立つ拡張機能がありますが、既存のデプロイに重大な変更を引き起こす可能性があります。これらの機能フラグはライフサイクルプロセスによって制御され、緩和と移行のための時間を提供します。これらのタイプのフラグは、既存のプロジェクトでは無効になり、新しいプロジェクトでは有効になります。

例)

- 異なるコードを生成することで既存のプロジェクトを壊し、バックエンドの展開が必要になる。
- 変更されたリソースのプッシュ操作では、リソースの再作成が必要となり、データ消失につながる可能性がある。
- 変更されたリソースのプッシュ操作は、クライアントアプリケーションを操作可能にするためにデータの埋め戻しが必要になる。
- クライアントアプリケーション用に生成されたコードは、新しくプッシュされたバックエンドと互換性があるように、再構築と再パブリッシュが必要になる。

### 実験

実験的な機能フラグは、特定の機能の実験を可能にし、Amplify CLIチームにフィードバックを提供するためのものです。本番環境でこれらの機能を有効にしないことを強くお勧めします。

実験的な機能の結果は、次のようになります。
- その機能が製品化され、リリースタイプの機能フラグに変更される。
- 実験的な機能は製品化されず、コードとともにコードベースから削除されます。

