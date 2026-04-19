# AWS：VPC環境でのWebサーバ構築と通信制御の検証

## 目的

AWSの基本サービス（VPC、EC2）の構築手順を習得し、リージョン選択やキュリティグループによる通信制御の挙動を実機で確認する。

## 構成

- **クライアント環境**: Ubuntu 24.04 LTS（ローカルPC）
- **クラウド環境**: AWS（VPC、EC2、IAM、Security Group）
- **リージョン**: 東京（ap-northeast-1）
- **VPC**: 10.0.0.0/16
- **Subnet**: パブリックサブネット
- **EC2 OS**: Amazon Linux 2023
- **Middleware**: Apache、nginx

## 構成図

<img width="957" height="539" alt="AWS-Webserver20260418 drawio" src="https://github.com/user-attachments/assets/f3e94d5f-77af-483c-9e40-30d49f667ee4" />

## 実施内容と結果

### 1. ネットワーク構築

- **リージョン設定の修正**: 当初、デフォルト設定のままシドニーリージョン（ap-southeast-2）でVPCを作成してしまった。実機操作においては、利用目的に応じた適切なリージョン選択が必要であることを学び、リソースを一度削除した上で、改めて**東京リージョン**にて再構築を実施。
- **VPC構成**: 東京リージョンにてVPC（10.0.0.0/16）及びインターネット通信可能にしたパブリックサブネットを作成。
- **サブネット**: ルートテーブルを編集し、パブリックサブネットを構成。

### 2. サーバ構築とリモート操作

- **EC2の構築**: セキュリティグループでSSH(22)とHTTP(80)の許可設定を行ったEC2インスタンス（Amazon Linux 2023）を起動。
- **SSH接続**: ローカルのUbuntuターミナルから、鍵認証を用いてEC2に接続。（①chmod 400 秘密鍵のパス　②ssh -i 秘密鍵のパス ec2-user@EC2のパブリックIP）
- **Webサーバ構築(Apache)**: ①sudo dnf update -y　②sudo dnf install -y httpd
- **Webサーバ起動と自動起動設定(Apache)**: ①sudo systemctl start httpd　②sudo systemctl enable httpd
- **動作確認**: ブラウザで「`http://EC2のパブリックIP`」を指定し、Apacheのテストページが出れば成功。
- **HTMLで簡易なWebページ作成**: ①sudo vi /var/www/html/index.html　②`<h1>`などのタグを使って、簡易なWebページ作成。

### 3. 通信制御の検証（セキュリティグループ）

- **HTTP(80)許可設定**: ブラウザから作成したWebページが表示されていることを確認。
- **ルール削除**: セキュリティグループからHTTP許可を削除し、即座にアクセス不可になることを確認。
- **ステートフル性の理解**: セキュリティグループの「戻りの通信を自動で許可する」特性を理解。

### 4. ミドルウェアの切り替え検証

- **Apacheからnginxへの切り替え**: ①sudo systemctl stop httpd　②sudo systemctl disable httpd　③sudo dnf install -y nginx　④sudo systemctl start nginx　⑤sudo systemctl enable nginx
- **動作確認**: ブラウザで「`http://EC2のパブリックIP`」を指定し、nginxのテストページが出れば成功。

## 課題と学び

- **リージョン選択の重要性**: クラウド操作の第一歩として、常に現在のリージョンを確認することを習慣付ける必要がある。
- **実機検証の有用性**: セキュリティグループのルール追加・削除がリアルタイムで反映されることを確認でき、経験を伴う理解に変えられた。
