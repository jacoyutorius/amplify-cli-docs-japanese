# インストール

## Amplify CLIをインストールする

Amplify Command Line Interface (CLI)はAWSクラウドサービスを構築するための統一されたツールチェーンです。
それではAmplify CLIをインストールしてみましょう。

**NPM**

```bash
npm install -g @aws-amplify/cli
```

**cURL(Mac and Linux)**

```bash
curl -sL https://aws-amplify.github.io/amplify-cli/install | bash && $SHELL
```

**cURL(Windows)**

```bash
curl -sL https://aws-amplify.github.io/amplify-cli/install-win -o install.cmd && install.cmd
```

### インストールの前提条件

- マシンに[Node.js](https://nodejs.org/en/download/)と[NPM](https://docs.npmjs.com/getting-started)があらかじめインストールされている必要があります。
- ターミナルまたはコンソールウィンドウにて `node -v` と `npm -v` を実行し、Node.jsのバージョンが12.x以上、npmのバージョンが6.x以上であることを確認してください。
- [AWSアカウントを作成してください](https://portal.aws.amazon.com/billing/signup?redirect_url=https%3A%2F%2Faws.amazon.com%2Fregistration-confirmation#/start)。この後の手順に沿って作業を進めるにはAWSアカウントが必要です。

## Amplify CLIの設定

Amplify CLIをローカルマシンにセットアップするにはAWSアカウントとの接続が必要です。

### オプション1: ビデオガイドを見る

Amplify CLIのインストールと設定方法については、以下のビデオをご覧いただくか、次のセクションに進んで、ステップバイステップの指示に従ってください。

<iframe src="https://www.youtube-nocookie.com/embed/fWbM5DLh25U" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


### オプション:2 以下の手順に従って操作をする

以下のコマンドを実行してAmplifyの設定をします。

```bash
amplify configure
```

`amplify configure` を実行するとAWSコンソールにサインインするよう求められます。

サインインすると、Amplify CLIはIAMユーザーを作成するよう要求します。

> Amazon IAM (Identity and Access Management) は、AWSのユーザーとユーザー権限を管理することができます。Amazon IAMの詳細については[こちら](https://aws.amazon.com/jp/iam/)をご覧ください。

```bash
Specify the AWS Region
? region:  # Your preferred region
Specify the username of the new IAM user:
? user name:  # User name for Amplify IAM user
Complete the user creation using the AWS console
```

AppSyncやCognito等のAWSリソースを作成できるように`AdministratorAccess-Amplify`権限でアカウントをIAMユーザーを作成します。

![https://docs.amplify.aws/images/user-creation.gif](https://docs.amplify.aws/images/user-creation.gif)

IAMユーザーを作成した際に発行された`accessKeyId`と`secretAccessKey` をAmplify CLIと接続します。

```bash
Enter the access key of the newly created user:
? accessKeyId:  # YOUR_ACCESS_KEY_ID
? secretAccessKey:  # YOUR_SECRET_ACCESS_KEY
This would update/create the AWS Profile in your local machine
? Profile Name:  # (default)

Successfully set up the new user.
```

```
他のデバイスで使用されている既存のIAMユーザーを使用するのではなく、Amplify CLIをインストールするすべてのデバイスに対して新しいIAMユーザーを作成することをおすすめします。
各マシンに個別のIAMユーザーを設定することで、アプリのデプロイを中断することなく、最高レベルの可視性と制御を提供し、必要に応じて個々のマシンのアカウントを無効にすることができます。
```

### フロントエンドプロジェクト内で作業する

CLIをインストールしたら、Javascript・iOS・Androidのプロジェクトのルートディレクトリに移動し、`amplify init`を実行してAmplifyを有効化します。
いくつかの設定に関する質問の後、いつでも`amplify help`を使用して、全体的なコマンド構造を確認することができます。
機能を追加する準備ができたら、`amplify add <category>`を実行します。
