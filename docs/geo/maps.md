https://docs.amplify.aws/cli/geo/maps/

# 地図

Amplifyの `geo` カテゴリを使用するとアプリケーションで地理空間データを視覚化するために使用されるマップリソースを作成することができます。

フィードバックや問題については、[こちら](https://github.com/aws-amplify/amplify-cli/issues)からお問い合わせください。

## 新しい地図をセットアップする

プロジェクトのルートディレクトリで以下のコマンドを実行することで新しい地図リソースを作成することができます。

```bash
amplify add geo
```

```bash
? Select which capability you want to add:
> Map (visualize the geospatial data)
  Location search (search by places, addresses, coordinates)
```

`auth` カテゴリのリソースを作成していない場合、Amplify CLIはauthカテゴリのリソースも作成するようガイドします。
以下で説明するように`auth` カテゴリは地図をレンダリングするための適切なアクセス許可を認証済みユーザー、およびゲストユーザーに付与するために必要です。

次に地図の名前を設定します。

```
? Provide a name for the Map:
> StreetsMap
```

## 地図のアクセス権限

次に地図へのアクセス権限を設定し利用者に地図のレンダリングを許可します。ユーザーの認証状態に基づいて権限の範囲を指定することができます。

```bash
? Who can access this Map?
❯ Authorized users only
  Authorized and Guest users
```

認証済みのユーザーのみに地図のレンダリングを許可したい場合は `Authorized users only`を選択します。

認証済みユーザーだけでなく、未認証のユーザーに対しても地図のレンダリングを許可する場合は `Authorized and Guest users` を選択します。

詳細についてはこちらを参照してください。[マップリソースをレンダリングするための権限](https://docs.aws.amazon.com/ja_jp/location/latest/developerguide/security_iam_id-based-policy-examples.html#security_iam_id-based-policy-examples-get-map-tiles)

## 料金プラン

料金プランは`RequestBasedUsage`に設定されます。価格プランの詳細については、[Amazon Location Service の料金](https://aws.amazon.com/jp/location/pricing/)と[AWS のサービス条件 (82.5 セクション) ](https://aws.amazon.com/jp/service-terms/)を確認することをお勧めします。

### 地図の料金プランを `RequestBasedUsage` に更新する

地図の料金プランは、プロジェクト内の `amplify/backend/amplify-meta.json` にあるプロジェクト メタデータ ファイルの `geo/<mapID>/pricingPlan` 属性から確認できます。

Amplify CLI のバージョンは、`amplify -v` を使用して確認できます。

Note:
Amplify CLI バージョン `7.6.8` 以前を使用していて、料金プランが `MobileAssetTracking` または `MobileAssetManagement` に設定されたマップがアプリケーションに追加されている場合は、次の手順に従って料金プランを更新してください。

1. `npm i -g @aws-amplify/cli` を使用して、Amplify CLI をバージョン `7.6.9` 以降にアップグレードします。
2. `amplify update geo` を実行し、アセットベースの料金プランでマップを選択します。既に持っているマップと同じ構成を選択します。
3. `amplify push` を実行して、バックエンド リソースを更新します。

## 高度な設定

オプションで地図のスタイルとデータプロバイダを設定できます。

### 地図のスタイルと地図データプロバイダ

地図リソースのスタイルを選択できます。使用可能なスタイルと、地理空間データのデータプロバイダーが表示されます。これらのスタイルの詳細については、[Amazon Location Servicesのドキュメント](https://docs.aws.amazon.com/ja_jp/location/latest/APIReference/API_MapConfiguration.html)を参照してください。

Note:
アプリケーションが、ビジネスで使用する資産 (配送車両や従業員など) を追跡またはルーティングする場合、地理位置情報プロバイダーとして `HERE` のみを使用できます。
詳細については[AWS のサービス条件 (82.5 セクション) ](https://aws.amazon.com/jp/service-terms/)を参照してください。

```bash
? Specify the map style:
❯ Streets (data provided by Esri)
  Berlin (data provided by HERE)
  Explore (data provided by HERE)
  ExploreTruck (data provided by HERE)
  Topographic (data provided by Esri)
  Navigation (data provided by Esri)
  LightGrayCanvas (data provided by Esri)
  DarkGrayCanvas (data provided by Esri)
  Imagery (data provided by Esri)
```

このプロパティを明示的に設定したくない場合は、`Streets (data provided by Esri)` がマップ スタイルの設定に使用されるデフォルトの設定値となります。

### デフォルトの地図をセットアップする

`amplify add geo` を実行して複数のマップを追加した場合、最後に追加された地図がデフォルトになります。ただし、現在の地図をアプリケーションのデフォルトにするかどうかを選択できます。

```bash
? Set this Map as the default? It will be used in Amplify Map API calls if no explicit reference is provided.
> No
```

`NO` を選択すると、以前に設定されたデフォルトが保持されます。

以上です！これでアプリケーションでマップをレンダリングできるようになりました。[ここ](https://docs.amplify.aws/lib/geo/maps/q/platform/js/)に記載されているライブラリのドキュメントに従ってください。

