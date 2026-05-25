# インフラエンジニア学習ポートフォリオ

未経験からインフラエンジニアになることを目指し、職業訓練校に通いながら、LinuxとAWSを中心に学習内容しています。
実機検証を通じて学習したことをGitHubにまとめています。
本日(2026/05/24)、学習開始から92日目を達成しました。

## 資格

- **LPIC-1**（2026年4月　合格）
- **AWS Certified Solutions Architect - Associate**（2026年5月　合格）

## 制作物①

- [AWS：VPC環境でのWebサーバ構築と通信制御](./AWS-Webserver-Build.md)

### 構成図

<img width="957" height="539" alt="AWS-Webserver20260418 drawio" src="https://github.com/user-attachments/assets/96368ddc-8d19-4743-a8b2-2eb26b4ff307" />

### 主な内容

- VPC構築
- EC2によるWebサーバ構築
- ローカルPC(Ubuntu)からのSSH接続
- セキュリティグループによる通信制御
- ミドルウェア比較検証（Apache/nginx）

## 制作物②

- [AWS：S3静的ウェブサイトホスティングによるサーバレスWeb公開](./AWS-S3-StaticSite-Build.md)

### 構成図

<img width="690" height="235" alt="AWS-S3-StaticSite20260419 drawio" src="https://github.com/user-attachments/assets/24f1a981-589b-4c92-82e8-7544bd2fcd0c" />

### 主な内容

- EC2を使わず、S3のホスティング機能を利用し、高速且つ低コストでWebページを公開
- バケットポリシーによる権限管理
- Webページの日本語の文字化け対策（HTML構造）

## 制作物③

- [AWS：S3 + CloudFrontによる静的Webサイト公開（Basic認証付き）](./AWS-S3-CloudFront-BasicAuth-WebSite.md)

### 構成図

<img width="1427" height="464" alt="AWS-S3-CloudFront-BasicAuth-WebSite drawio" src="https://github.com/user-attachments/assets/d5442a13-6b00-4eee-9e4d-52e55c75453d" />

### 主な内容



## 日々の学習ログ

日々の詳細な学習記録は、各Dayのファイルを参照。

- [最新のログ：Day0092（SAA試験合格）](./Day0092.md)
- [Day0001〜Day0092はこちら](https://github.com/Nittatsu447812/infra-study-log)
