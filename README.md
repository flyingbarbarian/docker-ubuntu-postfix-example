# docker-ubuntu-postfix-example
DockerでPostfixを動かしたい人の為の、Dockerfileの実装例です。

下記の二点に焦点をあてた実装例です。
1. Debian系のDockerコンテナにPostfixをインストールする。
2. SMTPリレーでメールを送信する。

そこに焦点をあてたので、それ以外の多くの部分を省いています。
1,2の目的を達成する最低限のコードしか書いていません。
**全くセキュアな実装ではありません。**
必要に応じてmain.cfにコードを足してみて下さい。

また、Mailtrapの使用を念頭に作っています。

# 使い方
1. ダウンロードして下さい。
2. `configs/main.cf`にSMTPリレーホストの情報を書いて下さい。
3. ディレクトリ`configs/`にファイル`sasl_passwd`を作成し、SMTPリレーホストのpasswordなどを書いて下さい。
4. `docker-compose build --no-cache`でイメージをビルドして下さい。
5. `docker-compose up -d`でコンテナが起動します。

これで、コンテナ内のPostfixからメールの送信ができます。

例
```
sendmail your-mail-address@example.com
From:your-mail-address@example.com
To:your-mail-address@example.com
Subject:Hello World

Hello World

.
```
