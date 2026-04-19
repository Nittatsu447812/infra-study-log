# インフラエンジニア学習ポートフォリオ

未経験からインフラエンジニアになることを目指し、職業訓練校に通いながら、LinuxとAWSを中心に学習内容しています。
実機検証を通じて学習したことをGitHubにまとめています。
本日(2026/04/18)、学習開始から56日目を達成しました。

## 資格

- **LPIC-1**（2026年4月　合格）
- **AWS Certified Solutions Architect - Associate**（2026年5月　受験予定、現在学習中）

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


## 日々の学習ログ

日々の詳細な学習記録は、各Dayのファイルを参照。

- [最新のログ：Day0056（AWS操作開始）](./Day0056.md)
- [Day0001〜Day0055はこちら](https://github.com/Nittatsu447812/infra-study-log)
