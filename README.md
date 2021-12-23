# docker-ubuntu-postfix-example
DockerでPostfixを動かしたい人の為の、Dockerfileの実装例です。

下記の二点に焦点をあてた実装例です。
1. Debian系のDockerコンテナにPostfixをインストールする。
2. SMTPリレーでメールを送信する。

そこに焦点をあてたので、それ以外の多くの部分を省いています。
1,2の目的を達成する**最低限のコード**しか書いていません。
必要に応じてmain.cfにコードを足してみて下さい。

SMTPリレーにはMailtrapの使うことを念頭に作っています。

# 使い方
1. ダウンロードして下さい。
2. `configs/main.cf.example`を`configs/main.cf`にファイル名変更して、SMTPリレーホストの情報を書いて下さい。
3. `configs/sasl_passwd.example`を`configs/sasl_passwd`にファイル名変更して、SMTPリレーホストの認証情報などを書いて下さい。
4. `docker-compose build --no-cache`でイメージをビルドして下さい。
5. `docker-compose up -d`でコンテナが起動します。
6. `docker exec -it docker-ubuntu-postfix-example-container /bin/bash`でコンテナにログインできます。

これで、コンテナ内のPostfixからメールの送信ができます。

例
```
$ sendmail your-email@example.com
From:your-email@example.com
To:your-email@example.com
Subject:Hello World

Hello World

.
```
