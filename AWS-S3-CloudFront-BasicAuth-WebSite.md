# AWS : S3 + CloudFrontによる静的Webサイト公開（Basic認証付き）

## 目的

AWSのS3とCloudFrontを利用して、静的WebサイトをHTTPSで公開する。
また、CloudFront Functionsを利用してBasic認証を実装し、限定公開サイトとして構築する。

## 使用サービス

- **Amazon S3**
- **Amazon CloudFront**
- **CloudFront Functions**
- **OAC(Origin Access Control)**

## 構成

- **ローカル環境**：Ubuntu 24.04 LTS
- **クラウド環境**：AWS
- **リージョン**：東京(ap-northeast-1)
- **配信方法**：CloudFront CDN
- **認証方法**：Basic認証
- **Webコンテンツ**：HTML・CSS・画像

## 構成図

<img width="1427" height="464" alt="AWS-S3-CloudFront-BasicAuth-WebSite drawio" src="https://github.com/user-attachments/assets/1e7c7c7c-2ae9-49cd-a612-11b93cc8de87" />

## 実施内容と結果

### 1.S3バケット作成

- 東京リージョンにS3バケットを作成
- パブリックアクセスブロックは有効のまま維持
- `index.html`と`style.css`と`imageフォルダ`をアップロード

### 2.CloudFrontディストリビューション作成

- 設定内容
  - **Origin**：S3
  - **OAC**：有効
  - **HTTPS**：有効
  - **Default Root Object**：`index.html`

- 結果
  - CloudFront経由でWebページ表示成功

### 3.OACによるS3非公開化

CloudFrontのみがS3へアクセスできる構成を作成

- 学んだこと
  - S3を直接パブリック公開しなくても、CloudFront経由で配信できることを理解した

### 4.CloudFront FunctionsによるBasic認証

CloudFront Functionsを作成し、Viewer Requestに関連付け

- 実装内容
  - Authorizationヘッダを確認
  - 一致しない場合は401 Unauthorizedを返却
  - Basic認証画面を表示

- 認証情報
  - **ID**：*****
  - **Password**：********

### 5.動作確認

- 確認内容
  - CloudFront URLへアクセス
  - Basic認証画面表示
  - ID/PW入力
  - Webページ表示成功

- 結果
  - Basic認証付き限定公開サイトとして動作確認完了
 
<img width="1041" height="1028" alt="Screenshot from 2026-05-26 00-59-06" src="https://github.com/user-attachments/assets/023a4837-4f7a-4ab3-81bb-c4aa77234bd5" />

## 課題と学び

- CloudFrontはコンテンツをキャッシュするため、S3更新が即時反映されないことがある
- OACを利用することで、S3を直接公開せずに配信できる
- CloudFront Functionsは軽量な認証処理に適している
- Viewer Requestで認証処理を行うことで、S3到達前にアクセス制御できる

## 今後追加したいこと

- Route53 + 独自ドメイン
- AWS WAF
- Geo Match
- アクセスログ取得
- レスポンシブ対応
- ポートフォリオサイト化
